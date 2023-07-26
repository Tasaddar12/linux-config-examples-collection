[**SELinux home**](/Security/SELinux.md)
## Disable SELinux
***
### References:
- [Redhat Guide](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/selinux_users_and_administrators_guide/sect-security-enhanced_linux-enabling_and_disabling_selinux-dracut-parameters)
- Redhat solution (https://access.redhat.com/solutions/3176)
- Ubuntu 22.04 Jammy selinux-config-enforcing (https://manpages.ubuntu.com/manpages/jammy/man8/selinux-config-enforcing.8.html)
- Ubuntu 22.04 Jammy selinux (https://manpages.ubuntu.com/manpages/jammy/man8/selinux.8.html)

### Steps:
**_Backup `/boot/grub2/grub.cfg`_**
```bash
sudo cp -p /boot/grub2/grub.cfg /root/grub.bak
```

**Open `/etc/default/grub`** and add `selinux=0` to the end of **`GRUB_CMDLINE_LINUX`** _not recommended to ever do, use permissive mode_
```
GRUB_CMDLINE_LINUX="crashkernel=1G-4G:192M,4G-64G:256M,64G-:512M resume=/dev/mapper/cs-swap rd.lvm.lv=cs/root rd.lvm.lv=cs/swap rhgb quiet selinux=0"
```

**Make config and reboot**
```bash
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
sudo reboot now
```

**Verify is disabled**
```bash
getenforce
```

## See Also:
***

