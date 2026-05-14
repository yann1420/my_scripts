1. Generate the Missing Locale On Debian, Ubuntu, and Mint, the locales package must be configured.

> **sudo dpkg-reconfigure   locales**

Select the desired locale (e.g., en_US.UTF-8) and ensure it is checked. Alternatively, edit /etc/locale.gen, uncomment the desired locale line, and run:

> **sudo locale-gen**

2. Verify Environment Variables If the locale is generated but the error persists, your environment variables may be pointing to the wrong value. Check your current settings with locale. If LC_ALL is unset or incorrect, set it explicitly:

**export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8**

3. Permanent Configuration To make these changes persistent across reboots, add the variables to your shell profile (~/.bashrc, ~/.zshrc) or system-wide configuration files:

System-wide: Edit /etc/default/locale or /etc/locale.conf and add:
**LANG=en_US.UTF-8
LC_ALL=en_US.UTF-8**

User-specific: Add export LC_ALL=en_US.UTF-8 and export LANG=en_US.UTF-8 to ~/.bashrc or ~/.zshrc. 
4. SSH-Specific Issues If this error appears only when connecting via SSH, your client might be sending incompatible locale variables.

Client-side: Edit /etc/ssh/ssh_config (or ~/.ssh/config) and comment out:
 SendEnv LANG LC_* 

Server-side: Edit /etc/ssh/sshd_config and ensure AcceptEnv LANG LC_* is commented out or removed, then restart the SSH service. 
