# Git Basics
## Set config values
git config --local user.email "testemail@gmail.com"

git config --local user.name "YesInAJiffy"

### List config values
git config --local --list

## Create a new repository on the command line
echo "# RestAPI" >> README.md

git init

git add .

git commit -m "first commit"

git branch -M main

git remote add origin https://github.com/YesInAJiffy/RestAPI.git

git push -u origin main


## Switch to existing branch in Git


gitbasics $git checkout dev

branch 'dev' set up to track 'origin/dev'

Switched to a new branch 'dev'

gitbasics $git branch

* dev

  main


