# snippets
Personal development snippets useful for day to day work

### Bash
```bash
# Bash clear command line
# Clean up the line: You can use Ctrl + U to clear up to the beginning.
# Clean up the line: Ctrl + A Ctrl + K to wipe the current line in the terminal.
# Cancel the current command/line: Ctrl + C .
# Recall the deleted command: Ctrl + Y (then Alt + Y )
# Go at the beginning of the line: Ctrl + A.
```

Find files with specific text inside
```bash
grep -R -H "FlowFixType" ./frontend/src | cut -d ' ' -f 1
# no duplicates
grep -R -H "FlowFixType" ./frontend/src | cut -d ' ' -f 1 | sort -u
```

### GIT
```bash
# update with rebase
git pull --rebase

# create new branch
git checkout -b new_branch

# push local branch to remote
# -u --set-upstream will set up the tracking information during the push.
git push -u origin <branch>

# remove local branch
git branch -d branch_to_delete

# remove remote branch
git push origin --delete remote_branch_to_delete
git push origin --no-verify --delete branch_name

# discard local modifications
git checkout -- file1 file2
git checkout -- . 

# Revert a specific file to a specific revision
git checkout c5f567 -- file1/to/restore file2/to/restore

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

# rebase -> change base(parent) of this branch to another
git rebase origin/develop # rebase on develop
git rebase -i origin/develop # rebase interactive mode, clean, pickup what you want, super cool

# That removes all local branches that have been deleted from remote (typically GitHub)
# Add --dry-run to merely see a list first to confirm.
git remote prune origin

```

### Docker

#### docker quick tour
```bash
# create docker file
touch Dockerfile

# build docker image with specified name:tag from current dir
docker build -t design-system .

# run docker container exposing port 80 to port 3000 on host
docker run --rm -d -p 3000:80/tcp frontend-initial

```

#### docker
```bash

# build
# docker build -t shykes/myapp:1.0.2 -t shykes/myapp:latest .
docker build -t frontend-initial .

# `run` - command in a new container
# -i interactive
# -t pseduo TTY 
# --detach , -d		Run container in background and print container ID
# --rm automatically remove the container when it exits

# run image
docker run -d -p 3000:80 frontend-initial

# exposes 8080/tcp from container to 127.0.0.1:80 on host
docker run -p 127.0.0.1:80:8080/tcp ubuntu bas

# runs bash on ubuntu:latest image
docker run --name ubuntu_bash --rm -i -t ubuntu bash
# runs bash on debian:latest image
docker run --name test -it debian

# `exec` - run a command in an existing container
docker exec -it ubuntu_bash bash

# `ps` - list running containers
# -a list all containers (not only running ones)
docker ps -a

# `rm` - removes container
# --force , -f		Force the removal of a running container (uses SIGKILL)
# --link , -l		Remove the specified link
# --volumes , -v	Remove the volumes associated with the container

docker rm $(docker ps -a -q) # remove all stopped containers
docker rm -f $(docker ps -a -q) # remove all containers (send SIGKILL to the running ones)

# remove a container and selectively remove volumes
docker rm -v hello

# `stop` - stops container
# stop all the running containers 
docker stop $(docker ps -a -q)

# `logs` - Fetch the logs of a container
# --follow , -f		Follow log output
# --since		Show logs since timestamp (e.g. 2013-01-02T13:23:37) or relative (e.g. 42m for 42 minutes)
# --tail	all	Number of lines to show from the end of the logs
# --timestamps , -t		Show timestamps
# --until		Show logs before a timestamp (e.g. 2013-01-02T13:23:37) or relative (e.g. 42m for 42 minutes)
docker logs service_name -f

# `attach` - Attach local standard input, output, and error streams to a running container
# Attach isn't for running an extra thing in a container, it's for attaching to the running process.
docker attach test

# `prune`
# --all , -a		Remove all unused images not just dangling ones
# --force , -f		Do not prompt for confirmation
# --volumes		Prune volumes
docker system prune -a -f --volumes

# remove dangling volumes
docker volume rm $(docker volume ls  -q --filter dangling=true)
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
```bash
# View registry info
npm view express
```

Linking
```bash
# 1. inside "module" folder you want to link to
npm link

# 2. inside package folder you want use linked "module"
npm link module

# check already linked modules
npm ls -g --depth=0 --link=true
```

Unlink
```bash
# 1. inside package folder where linked module is used
npm unlink --no-save module

# 2. inside linked module
npm unlink
```

### Node
#### Node CLI
```bash
# start node with preloaded module
node -r ./.pnp.js

# start debugging
# --inspect Listen on default address and port (127.0.0.1:9229)
# --inspect=[host:port] Listen on specified address and port
# --inspect-brk Break before user code starts
# (legacy from node 7.7.0) --debug or --debug-brk
node --inspect

# Spawn child process to run user's script under --inspect flag; and use main process to run CLI debugger.
node inspect script.js
```

### Powershell

```powershell
# remove folder recursively
Remove-Item -Recurse -Force some_dir
# alias
rm -r -fo some_dir
```

### SSH
```bash
# This starts a ssh tunnel session where a connection to port 9221 on your local machine will be forwarded 
# to port 9229 on remote.example.com. You can now attach a debugger such as Chrome DevTools or Visual Studio Code to localhost:9221
ssh -L 9221:localhost:9229 user@remote.example.com
```

### Electron
#### CLI helpers
```bash
# Extract asar files
npx asar extract app.asar destfolder 
```
