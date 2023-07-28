[**SELinux home**](/Security/SELinux.md)
## Apply SELinux fcontexts
***
### Quick Jump
- [References](#references)
- [httpd_sys_content_t example](#configure-httpd-sys-dir-context)
- [httpd_user_content_t example](#configure-httpd-user-dir-context)

### References:
- Ubuntu 22.04 semanage-fcontext (https://manpages.ubuntu.com/manpages/jammy/man8/semanage-fcontext.8.html)
- Linux Die httpd_selinux (https://linux.die.net/man/8/httpd_selinux)
- ServerFault httpd policies (https://serverfault.com/questions/701034/add-custom-allow-policy-in-selinux/701051#701051)
- Difference between httpd_sys_content_t and httpd_user_content_t (https://serverfault.com/questions/819856/difference-between-httpd-sys-content-t-httpd-user-content-t)

### Configure Httpd SYS Dir Context
```bash
semanage fcontext -at httpd_sys_content_t "/web(/.*)?" # Apply context to everything for /web
restorecon -R -v /web # Save / Set context

ls -Zd /web # Verify we have context set
```

### Configure Httpd USER Dir Context
```bash
# One of the following 2
semanage boolean --modify --on httpd_enable_homedirs # Allow homedirs to be used with httpd_user_content_t. This adds more security compared to httpd_sys_content_t on home webfiles
sesetbool -P httpd_enable_homedirs 1 # -P for saving the change

semanage fcontext -at httpd_user_content_t "/home/webuser/www(/.*)?" # Apply context to everything for /home/webuser/www
restorecon -Rv /home/webuser/www # Save / Set context
```


## See Also:
***
