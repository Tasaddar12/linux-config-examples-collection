[**SELinux home**](/Security/SELinux.md)
## Change Enforcing Mode
***
### References:
- [Redhat 9 temporary changes](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/configuring_basic_system_settings/assembly_configuring-system-security_configuring-basic-system-settings#proc_ensuring-the-required-state-of-selinux_assembly_configuring-system-security)
- [Redhat 9 permanant changes](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/using_selinux/changing-selinux-states-and-modes_using-selinux#changing-selinux-modes-at-boot-time_changing-selinux-states-and-modes)
- Ubuntu 22.04 Jammy selinux-config-enforcing (https://manpages.ubuntu.com/manpages/jammy/man8/selinux-config-enforcing.8.html)
- Ubuntu 22.04 Jammy setenforce (https://manpages.ubuntu.com/manpages/jammy/man8/setenforce.8.html)
- Man7 setenforce (https://man7.org/linux/man-pages/man8/setenforce.8.html)

## Temporary Solution
### Steps:
**Use `setenforce` command**
```bash
setenforce Enforcing | 1 # Enables Enforcing Mode
setenforce Permissive | 0 # Enables Permissive Mode
```

## Permanent Solution
### Steps:
**_Backup `/boot/grub2/grub.cfg`_**
```bash
sudo cp -p /boot/grub2/grub.cfg /root/grub.bak
```

**Open `/etc/default/grub`** and add `enforcing=0` or `enforcing=1` to the end of **`GRUB_CMDLINE_LINUX`** 
```
GRUB_CMDLINE_LINUX="crashkernel=1G-4G:192M,4G-64G:256M,64G-:512M resume=/dev/mapper/cs-swap rd.lvm.lv=cs/root rd.lvm.lv=cs/swap rhgb quiet enforcing=0 | 1"
```

**Make config and reboot**
```bash
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
sudo reboot now
```

**Verify we are in permissive or enforcing**
```bash
getenforce
```

## See Also:
***
- [Disable SELinux](disable-selinux.md)
