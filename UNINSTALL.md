# Uninstall
Sorry to see you go. There are two things you need to remove.

## Remove checking tools
```bash
rm /etc/init.d/vmware-check-tools
rm /etc/sysconfig/vmware-check-tools
rm /lib/modules/*/misc/vmware_tools.ver
```

## Remove the installed VMware tools
```bash
/usr/bin/vmware-uninstall-tools.pl
rm -rf /usr/lib/vmware-tools
rm -rf /etc/vmware-tools
```
