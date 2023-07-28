# Quick Links:
**Link to SELinux git** (https://github.com/SELinuxProject/selinux)

**Table of contents**
- [Security Home](/Security/README.md)
- [Commands](#commands)
- [Purpose of SELinux](#purpose-of-selinux)
- [Usage Examples](#usage-examples)

# Purpose of SELinux:
**Information is from _[Redhat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/configuring_basic_system_settings/assembly_configuring-system-security_configuring-basic-system-settings#con_managing-basic-selinux-settings_assembly_configuring-system-security)_**

Security-Enhanced Linux (SELinux) adds another layer of security which uses SELinux policies to determine what processes can access which files, directories, and ports.

SELinux has two possible states:
- **Disabled**: _<sup>Not recommended</sup>_
- **Enabled**: _<sup>Recommended to use **Permissive** mode when debugging / troubleshooting</sup>_
  - Enforcing: _<sup>Enforces loaded policies, denying access to everything that is not explicitly allowed. Default mode after installation</sup>_
  - Permissive: _<sup>Does not enforce loaded policies, but will log actions that break policies to `/var/log/audit/audit.log`. Default mode during installation</sup>_
 
# Usage Examples:
**Links to examples**
- [Disable Selinux](SELinux/disable-selinux.md)
- [Change Enforcing Modes](SELinux/change-enforcing-modes.md)
- [Applying fcontexts](SELinux/apply-fcontexts.md)





















