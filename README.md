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
#### docker-compose
### NPM

### Powershell

```powershell
# remove folder recursively
Remove-Item -Recurse -Force some_dir
# alias
rm -r -fo some_dir
```
