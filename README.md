# VMWare Tools recompiling system service
When running a Linux virtual machine on a VMWare Hypervisor you are adviced to install the VMWare Guest Tools on the virtual machine. But after every kernel upgrade you’ll have to recompile them. This can become a tedious task when you have a lot of virtual machines.
This system service will compile the VMWare Guest Tools once for every new kernel. It will not install the Guest Tools if they have never been installed manually and it will not keep them up to date, meaning that you still have to update manually when you upgrade the hypervisor.

# Installation
```bash
rsync -a --exclude=\*.md --exclude=.git . /etc/
chmod +x /etc/init.d/vmware-check-tools
chkconfig vmware-check-tools on
```