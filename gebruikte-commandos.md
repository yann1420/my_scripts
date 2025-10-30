## SSH access

### commands
```
ssh-keygen             # Step 1: Public and Private Key Generation

cd ~/.ssh
chmod 600 id_rsa       # Step 2:  Change Permissions

ssh-copy-id user@IP    # Step 3:  Configure Server

ssh user@IP            # step 4:  Verify access
```

### [How to Login to SSH Without A Password Using Private Key?](https://www.geeksforgeeks.org/linux-unix/how-to-login-to-ssh-without-a-password-using-private-key/)
