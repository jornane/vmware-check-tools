# VMware Tools recompile system service

> You don't need this anymore!  Most OSes have `open-vm-tools` in their repo, which works a lot better.

When running a Linux virtual machine on a VMware Hypervisor you are adviced to install the VMware Guest Tools on the virtual machine.
But after every kernel upgrade you’ll have to recompile them.
This can become a tedious task when you have a lot of virtual machines.

## What will it do
This system service will compile the VMware Guest Tools once for every new kernel.

## What will it not do
This system service will not install the Guest Tools if they have never been installed manually before, and it will not keep them up to date, meaning that you still have to update manually when you upgrade the hypervisor.
Maybe this feature will be added in the future.
Patches are welcome.

# Installation
## VMware Tools
In the vSphere client, choose **Guest** -> **Install/Upgrade VMware Tools**.

Execute the following script:
```bash
mkdir -p /mnt/sr0 \
&& mount /dev/sr0 /mnt/sr0 \
&& cd \
&& tar -xzvf /mnt/sr0/VMwareTools-*.tar.gz \
&& umount /mnt/sr0 \
&& rmdir /mnt/sr0 \
&& yum install -y kernel-headers kernel-devel perl gcc make eject \
&& vmware-tools-distrib/vmware-install.pl --default
```

## Recompile system service
```bash
#!/bin/sh
git clone git://github.com/yorn/VMware-check-tools.git
cp VMware-check-tools/init.d/* /etc/init.d/
cp VMware-check-tools/sysconfig/* /etc/sysconfig/
chmod +x /etc/init.d/VMware-check-tools
chkconfig VMware-check-tools on
rm -rf VMware-check-tools
```
