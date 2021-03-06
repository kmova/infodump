## Setting up local version
```
cd <code-base-dir>
git clone <git-project-url>
cd git-project
git config --global user.name "kmova"
git config --global user.email "kiran.mova@mayadata.io"
git config --global core.pager "less -r" 
git config -l
```

## List and switch to remote branch
```
git fetch
git branch -r
git checkout <branch-name>
git branch
```

## Push the modified changes to remote branch
```
git status
git commit -a -m "<comment for checkin>"
git push
```

## Make changes in local branch and push it upstream
```
git branch alpha-skunkie
git checkout alpha-skunkie
git push --set-upstream origin alpha-skunkie
```

## Delete local and remove branch
```
git push origin --delete <branch_name>
git branch -d <branch_name>
```

## Clear dirty/temporary changes
```
git stash
git stash clear
git stash show
```

## Rebase forked with origin
```
git clone https://github.com/<forked-rep>.git
git remote add upstream https://github.com/<origin-rep>.git
git fetch upstream
git rebase upstream/master
#If conflicts are there resolve them and run "git resbase --continue"
#Commit your changes
git push -f
```

## Sqash commits using rebase
```
#specify the start commit id
#launches a editor - where you can select to "squash" or "pick" 
git rebase -i d04b4c59fe5ba484b4d10b1eaf32428329265b15
#should show that local branch has diverged from upstream
git status
git push -f
```


## Amend commit messages
```
git commit --amend
#modify the message in the editor
#should show that 1 commit on local branch has diverged from upstream
git status
git push -f
```

## Create new tag from current branch
```
git tag #check the tags
git tag -a <tag-name>
git push origin <tag-name>
```

## Create branch from tag
```
git tag #check the tags
git branch -r #check the branches
git checkout -b v0.6 0.6.0
git push --set-upstream origin v0.6
```

## Create branch from commit
```
git branch <new-branch-name> <commit-hash>
git checkout <new-branch-name>
git push --set-upstream origin <new-branch-name>
```

## Syncing a new branch from upstream into forked repo
```
git fetch upstream v0.7.x:v0.7.x
git checkout v0.7.x
git push --set-upstream origin v0.7.x
```
## Getting git log
```
git log --pretty=format:'- %s (%h) (@%an)' --date=short  --since="1 month"
```

## Install git-extras for working with commands like git changelog
```
sudo apt-get install git-extras
```


## Migrate repo using filter-repo

Example: migrate the subdirectories related to provisioner-localpv from existing repo github.com/openebs/maya to a new repo called github/com/kmova/dynamic-localpv-provisioner.

```
git clone --branch master --origin origin --progress -v https://github.com/openebs/maya.git
cd maya/
git filter-repo --path cmd/provisioner-localpv/ --path buildscripts/provisioner-localpv/
git log
git status
git remote add origin https://github.com/kmova/dynamic-localpv-provisioner.git
git branch -M develop
git push -u origin develop
```
