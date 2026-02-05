## SSH access

### commands
```
ssh-keygen             # Step 1: Public and Private Key Generation

chmod 600 ~/.ssh/id_rsa       # Step 2:  Change Permissions

ssh-copy-id user@IP    # Step 3:  Configure Server

ssh user@IP            # step 4:  Verify access
```

### [How to Login to SSH Without A Password Using Private Key?](https://www.geeksforgeeks.org/linux-unix/how-to-login-to-ssh-without-a-password-using-private-key/) [Or look here](https://linuxize.com/post/how-to-setup-passwordless-ssh-login/)

## DNS lookup 

### [How to Use dig and nslookup In Linux](https://www.tecmint.com/install-dig-and-nslookup-in-linux/)

### COMMANDS
```
sudo apt install dnsutils
```
## Install Nextcloud in Docker

### [Docker install](https://docs.docker.com/engine/install/)

### Nextcloud install [https://nextcloud.com/blog/how-to-install-the-nextcloud-all-in-one-on-linux/](https://nextcloud.com/blog/how-to-install-the-nextcloud-all-in-one-on-linux/)

### MacBook Air model A1466

insert live CD and select OS by pressing left ALT key after boot

### Completely Disable Suspend/Hibernate in Ubuntu 
1. Edit /etc/systemd/sleep.conf\
2. When file opens, scroll down and set following rules under [Sleep] section:

```
AllowSuspend=no
AllowHibernation=no
AllowSuspendThenHibernate=no
AllowHybridSleep=no



```
