# snippets
Personal development snippets useful for day to day work

### GIT
```bash
# update with rebase
git pull --rebase

# create new branch
git checkout -b new_branch

# remove local branch
git branch -d branch_to_delete

# remove remote branch
git push origin --delete remote_branch_to_delete

# discard local modifications
git checkout -- file1 file2
git checkout -- . 

# avoid repeated merge conflicts
git config --global rerere.enabled true

# fix last commit message
git commit --amend -m "New message"

# add forgotten file to the last commit
git add forgotten_file 
git commit --amend

# undo last two commits, keep changes
git reset HEAD~2
# undo last two commits, discard changes 
git reset --hard HEAD~2  
# reset to the origin and discard changes
git reset --hard origin/branch
```

### Docker
#### docker
```bash
# `run` - command in a new container
# -i interactive
# -t pseduo TTY 
# --rm removes container if exists
# ubuntu image name
# bash command

# runs bash on ubuntu:latest image
docker run --name ubuntu_bash --rm -i -t ubuntu bash
# runs bash on debian:latest image
docker run --name test -it debian

# `exec` - run a command in an existing container
docker exec -it ubuntu_bash bash

# `ps` - list running containers
# -a list all containers (not only running ones)
docker ps -a
```
#### docker-compose
```bash
# `up` - builds, (re)creates, starts, and attaches to containers for a service.
# -d detached
# -f config path (it's docker-compose param, not 'up' command)
# --build build images before starting containers.
docker-compose -f ./docker-compose.yml up -d --build
```
### NPM

### Powershell

```powershell
# remove folder recursively
Remove-Item -Recurse -Force some_dir
# alias
rm -r -fo some_dir
```
