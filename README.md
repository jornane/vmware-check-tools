# VMWare Tools recompile system service
When running a Linux virtual machine on a VMWare Hypervisor you are adviced to install the VMWare Guest Tools on the virtual machine. But after every kernel upgrade you’ll have to recompile them. This can become a tedious task when you have a lot of virtual machines.

## What will it do
This system service will compile the VMWare Guest Tools once for every new kernel.

## What will it not do
This system service will not install the Guest Tools if they have never been installed manually before, and it will not keep them up to date, meaning that you still have to update manually when you upgrade the hypervisor.
Maybe this feature will be added in the future. Patches are welcome.

# Installation
```bash
#!/bin/sh
git clone git://github.com/yorn/vmware-check-tools.git
cp vmware-check-tools/init.d/* /etc/init.d/
cp vmware-check-tools/sysconfig/* /etc/sysconfig/
chmod +x /etc/init.d/vmware-check-tools
chkconfig vmware-check-tools on
rm -rf vmware-check-tools
```
