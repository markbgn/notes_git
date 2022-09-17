# GitHub notes 
## Creating a NEW REPO:
1. Create a new directory for the project in github
2. Create the same repo locally on the computer as well
3. Navigate to the directory
4. `git init`
5. linking the local and the remote repo:
    `git remote add origin https://github.com/markbgn/[name of the repo].git`

## Pushing (uploading) changes:
1. `git add .` adds all files
or
2. `git add [file]` adds a specific file to the commit
3. `git commit -m "write comment here"`
4. `git push -u origin master`

## Pulling (downloading) changes:
1. `git pull <REMOTE> <name-of-branch>`

## Creating a branch
`git checkout -b <branch-name>`

## Pushing a branch
`git push -u <remote> <branch-name>`
