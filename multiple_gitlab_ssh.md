# ssh config for 2 gitlab accounts

### File paths
.ssh/config
.ssh/id_ed25519
.ssh/id_ed25519.pub
.ssh/id_ed25519_gitlab_second  
.ssh/id_ed25519_gitlab_second.pub


### generating key
```shell
ssh-keygen -t ed25519 -C "your-email@example.com" -f ~/.ssh/id_ed25519
ssh-keygen -t ed25519 -C "your-email-second@example.com" -f ~/.ssh/id_ed25519_gitlab_second
```

### config file (.ssh/config)
```shell
# First GitLab account
Host gitlab.com
    HostName gitlab.com
    User git
    IdentityFile ~/.ssh/id_ed25519

# Second GitLab account
Host gitlab-second
    HostName gitlab.com
    User git
    IdentityFile ~/.ssh/id_ed25519_gitlab_second
```


### usage
then when using commands use 
```shell
git clone git@gitlab-second:vishmay-code/project.git
```
and if first account then 
```shell
git clone git@gitlab.com:vishmay-code/project.git
```

### verifying which git config is used
```shell
ssh -T git@gitlab-second
```
or 
```shell
ssh -T git@gitlab.com
```

