# git commands

### Conflicts resolving

```shell
git checkout branch (where you want to merge)

git fetch
git pull

git merge origin/branch (which you want to merge in currently checkout branch)

git add .
git commit -m "msg"

git push
```

-------------------------------------------------------------------------------------

### Master merge by mistake

 just reset to the previous tag
```shell
git reset --hard v22.10.01
```

then in GitHub web app allow force push to master branch in settings and
```shell
git push --force
```

-------------------------------------------------------------------------------------

### Pull local branches which are ahead in repository

```shell
git fetch -p

for branch in $(git branch -vv | grep ': behind ' | sed '/*/{$q;h;d};$G' | tr -d '*' | awk '{print $1}'); do git checkout $branch && git merge --ff-only || break ; done
```

-------------------------------------------------------------------------------------

### Delete local branches which are deleted branches from repository

```shell
git fetch -p

for branch in $(git branch -vv | grep ': gone]' | sed '/*/{$q;h;d};$G' | tr -d '*' | awk '{print $1}'); do git branch -D $branch; done
```

-------------------------------------------------------------------------------------

### Deleting branches locally

```shell
git fetch -p

git branch --merged | egrep -v "(^\*|master)"  | xargs git branch -d
```

-------------------------------------------------------------------------------------

### Check conflicts

```shell
grep -rl --exclude-dir={'specs','tmp'} --include=*.{php,js,tpl,html,css}  --color  'axios'

grep -rl --exclude-dir={'public','node_modules'} --include=*.{js,html,css,scss,jsx}  --color  'axios'
```

-------------------------------------------------------------------------------------

### Change HTTP to SSH

```shell
git remote -v
```
and you shall see the output as below
```shell
origin  https://gitlab.com/vishmaycode/vishmaycode.git (fetch)
origin  https://gitlab.com/vishmaycode/vishmaycode.git (push)
```

then 
```shell
git remote set-url origin git@gitlab.com:vishmaycode/vishmaycode.git
```

then verify
```shell
ssh -T git@gitlab.com
```

-------------------------------------------------------------------------------------

### Creating SSH keys

```shell
ssh-keygen -t ed25519 -C "your-email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub  (copy this and add in gitlab)
```
