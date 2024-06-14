## **Essential Git Commands**

### **Basic Commands**

- `**git --version**`: Display the installed Git version.
- `**git help**`: Get help information on Git commands.
- `**git init**`: Initialize a new Git repository.
- `**git clone URL**`: Clone a repository from a remote URL.
- `**git status**`: Show the working directory status.
- `**git add FILE**`: Add files to the staging area.
- `**git commit -m "message"**`: Commit changes with a message.
- `**git log**`: View commit history.
- `**git diff**`: Show changes between commits, commit and working tree, etc.
- `**git reset**`: Reset current HEAD to a specified state.
- `**git rm FILE**`: Remove files from the working directory and staging area.
- `**git mv OLD_NAME NEW_NAME**`: Rename or move files.

### **Branching and Merging**

- `**git branch**`: List, create, or delete branches.
- `**git checkout BRANCH**`: Switch to a branch.
- `**git merge BRANCH**`: Merge a branch into the current branch.
- `**git branch -d BRANCH**`: Delete a branch.
- `**git rebase BRANCH**`: Reapply commits on top of another base tip.
- `**git cherry-pick COMMIT**`: Apply the changes introduced by some existing commits.

### **Remote Repositories**

- `**git remote**`: Manage set of tracked repositories.
- `**git remote add NAME URL**`: Add a new remote repository.
- `**git fetch REMOTE**`: Fetch branches and/or tags from the remote repository.
- `**git pull REMOTE BRANCH**`: Fetch from and integrate with another repository or a local branch.
- `**git push REMOTE BRANCH**`: Update remote refs along with associated objects.

### **Stashing and Cleaning**

- `**git stash**`: Stash the changes in a dirty working directory away.
- `**git stash apply**`: Apply the latest stashed changes.
- `**git stash list**`: List all stashed changes.
- `**git clean**`: Remove untracked files from the working directory.

### **Viewing and Comparing**

- `**git show COMMIT**`: Show various types of objects.
- `**git log --oneline**`: View commit history in a compact form.
- `**git diff COMMIT1 COMMIT2**`: Show changes between two commits.
- `**git blame FILE**`: Show what revision and author last modified each line of a file.
- `**git tag**`: Create, list, delete, or verify a tag object.

## **Intermediate Git Commands**

### **Advanced Branching and Merging**

- `**git branch --merged**`: List branches that have been merged into the current branch.
- `**git branch --no-merged**`: List branches that have not been merged.
- `**git merge --squash BRANCH**`: Merge a branch into the current branch and squash commits.

### **Remote Repositories**

- `**git remote rename OLD_NAME NEW_NAME**`: Rename a remote repository.
- `**git remote remove NAME**`: Remove a remote repository.
- `**git fetch --all**`: Fetch all branches from all remotes.
- `**git push --all**`: Push all branches to the remote repository.
- `**git pull --rebase**`: Fetch from and integrate with another repository or a local branch using rebase.

### **Stashing**

- `**git stash save "message"**`: Save changes to stash with a message.
- `**git stash pop**`: Apply the latest stashed changes and remove them from stash.
- `**git stash drop**`: Remove a single stashed state from the stash list.

### **Submodules**

- `**git submodule add URL**`: Add a submodule.
- `**git submodule update**`: Initialize, fetch and checkout submodule(s).
- `**git submodule init**`: Initialize local configuration file.

## **Advanced Git Commands**

### **Rewriting History**

- `**git rebase -i HEAD~N**`: Interactively rebase the last N commits.
- `**git reset --hard COMMIT**`: Reset the working directory to match a specific commit.
- `**git reflog**`: Show the history of changes to the tip of branches.
- `**git cherry-pick -n COMMIT**`: Apply changes introduced by existing commits without committing.

### **Working with Patches**

- `**git format-patch COMMIT**`: Prepare patches for email submission.
- `**git apply PATCH**`: Apply a patch to files and/or to the index.

### **Bisecting**

- `**git bisect start**`: Start the bisecting process.
- `**git bisect bad**`: Mark the current state as bad.
- `**git bisect good COMMIT**`: Mark a known good commit.
- `**git bisect reset**`: Reset bisect state.

### **Advanced Configuration**

- `**git config --global user.name "Name"**`: Set the global username.
- `**git config --global user.email "Email"**`: Set the global email address.
- `**git config --global color.ui auto**`: Enable automatic command output coloring.

### **Hooks**

- `**git hook**`: Manage git hooks.
- `**git hook run HOOK**`: Run a specific hook.
- `**git hook list**`: List all hooks.
