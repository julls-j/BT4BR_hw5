# BT4BR_hw5
name: Julia Janecka  
date: 21.11.2026

This repository is an assignment for BT4BR class.

## Linking a computer with GitHub  
1. Chech the SSH keys that exist in the computer:  
  ```ls -al ~/.ssh```
2. Create a new key that will be provided to GitHub later on:  
  ```ssh-keygen -t ed25519 -C "your-email@example.com```  
  > * now you can see your key in the SSH keys  
  > * to check the content of the public key: 
    ```cat ~/.ssh/id_ed25519.pub```
3. Registering the public key on GitHub:  
  > Profile > Settings > SSH and GPG keys > New SSH key > Add SSH key
## Making a local copy of the repository  
1. Click on "Code" and copy the URL of your repository.  
2. Open the terminal, navigate to the directory of choice, and **clone** the repository:  
  ```git clone copied_link```

## Adding files to the repository
1. Create a (ex. python) script with a text editor (ex. nano).
2. Start tracking the file with git:  
  ```git add file_name.py```
  > * If you want to track _all files in the directory_ a once: 
    ```git add .```
3. Commit (add a **message**!!):  
  ```git commit -m "Write your message here."```
  > * if you make a typo in the message, you can modify it once by:
  ```git commit --amend -m "Corrected message."```  
  or run: `git commit --amend` to edit message in your default text editor.
4. Save the changes in the cloud (GitHub)
```git push origin main```

## Editing files
1. See differences with last committed version:
```git diff```
2. Stage all modified files:
```git add -u```  
3. If you chech the status `git status` it will show you that the file has "changes to be committed". The snapshot has not yet been created.

## Commiting changes
1. Create a "snapshot" of the current files:
```git commit -m "Your message"```
2. Save changes on GitHub:
```git push```
3. You can see the changes and compare versions in GitHub.

## Branching and merging
**Branching** is creating an independent line of development within a repository so you can work without affecting the main codebase. If you are happy with the new branch, you can later **merge** it with the main one.

1. Create new branch: ```git branch new_branch```
2. Change working branch: ```git checkout new_branch```
3. Edit a file
4. Stage and commit the canges to the branch:  
```
git add -u file_name.py  
git commit -m "your message" 
git push origin new_branch
```
5. Compare the 2 branches: ```git diff main..new_branch```
6. Go back to main branch: ```git checkout main```
7. Merge the branch to main:  
```
git merge new_branch
git push
```

## Restoring
1. See all the commits:
```git log --oneline```
2. Find the commit id you want to restore:
`git checkout <commit ID>`
3. Check the file content in the previous commit:
`cat file_name.py`
> Now we are in a state called 'detached HEAD', we are visualizing an older commit, but the main branch is still with the same modifications we made before.
4. Create a branch from this previous commit:
`git switch -c branch_name`
> * Modify the file.
> * Save the changes:
> ```
> git add -u file_name.py
> git commit -m "Your message"
> ```
5. Compare the two branches:
```
git switch main
git diff main..branch_name
```
6. Make the recovered version the main:
> Check that you have no other uncommited changes, if you do, you won't be able to merge branches: `git status`  
Replace the content of `main` with the context of the new branch:  
`git restore --source=branch_name --staged --worktree :/`
> `:/` is telling Git to apply the changes in the whole repository file structure
> If you only want to restore a single file:  
```git restore --source=branch_name --staged --worktree -- path/to/file.ext```
Finally, create a new commit with the changes:  
`git commit -m "Your message"`







