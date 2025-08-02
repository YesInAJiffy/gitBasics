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



# Merge your commits to Remote Repository
---

### ✅ Step-by-Step Process

#### 1. **Make Changes Locally**
Edit files and stage them:
```bash
git add .
```

#### 2. **Commit Your Changes**
Create a commit with a message:
```bash
git commit -m "Describe your changes"
```

#### 3. **Update Your Local Branch (Optional but Recommended)**
Before pushing, make sure your branch is up to date with the remote:
```bash
git pull origin main --rebase
```
This helps avoid conflicts and keeps history clean.

#### 4. **Push to Remote Repository**
Send your local commits to the remote:
```bash
git push origin main
```

---

### 🔄 Optional: Merge Another Branch Before Pushing

If you're working on a feature branch and want to merge it into `main` before pushing:

```bash
git checkout main
git merge feature-branch
git push origin main
```

Or, if you prefer a cleaner history:

```bash
git checkout feature-branch
git rebase main
git checkout main
git merge feature-branch
git push origin main
```

---

### 🧠 Summary

| Action         | Command                      | Purpose                              |
|----------------|------------------------------|--------------------------------------|
| Stage changes  | `git add .`                  | Prepare files for commit             |
| Commit         | `git commit -m "message"`    | Save changes locally                 |
| Rebase (optional) | `git pull --rebase`       | Sync with remote before pushing      |
| Merge (optional) | `git merge branch-name`    | Combine branches                     |
| Push           | `git push origin branch-name`| Upload commits to remote repository  |

