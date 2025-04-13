# how to set up and use the personal token from github

first go and create your token from github account by going to settings/developer settings/personal token

generate a token with prefered previlages 
repo for me

then copy that token as it can be only available till page gets close or refreshed. so keep it save in protonpass or anywhere

then go to the commandline and use the token copied as password whenever using the push pull or fetch command when asked for username and password

git push 

username: vishmay-k
password: token*********


### Using credentials helper

```shell
git config --global credential.helper cache
```
this will cache the next username and password and you wont have to remember the username password

to remove this setting the commands are
```shell
git config --global --unset credential.helper
```

to list configs
```shell
git config -l
```

