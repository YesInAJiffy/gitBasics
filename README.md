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



# Push vs Merge vs Rebase
Comparison of **`git push`**, **`git merge`**, and **`git rebase`**, highlighting their purposes, effects, and when to use each:

---

### 🔹 `git push`

- **Purpose**: Uploads your local commits to a remote repository.
- **Scope**: Remote (e.g., GitHub, GitLab).
- **Effect**: Makes your local changes available to others.
- **Example**:
  ```bash
  git push origin main
  ```

---

### 🔹 `git merge`

- **Purpose**: Combines changes from one branch into another.
- **Scope**: Local.
- **Effect**: Creates a **merge commit** that joins histories of both branches.
- **Example**:
  ```bash
  git checkout main
  git merge feature-branch
  ```

---

### 🔹 `git rebase`

- **Purpose**: Reapplies commits from one branch onto another base.
- **Scope**: Local.
- **Effect**: Rewrites commit history to create a linear progression.
- **Example**:
  ```bash
  git checkout feature-branch
  git rebase main
  ```

---

### 🆚 Summary Comparison

| Command      | Scope     | Purpose                          | History Impact         | Creates Merge Commit? | Use Case                          |
|--------------|-----------|----------------------------------|-------------------------|------------------------|-----------------------------------|
| `push`       | Remote    | Share local commits              | No change               | No                     | Upload changes to remote repo     |
| `merge`      | Local     | Combine branches                 | Preserves full history  | Yes                    | Collaborative development         |
| `rebase`     | Local     | Reapply commits on new base      | Rewrites history        | No                     | Clean up history before merging   |

---


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





---

Here's how you can perform **Merge** and **Rebase** operations in **Android Studio** using its built-in Git integration:

---

## 🔄 **Merge in Android Studio**

### Steps:
1. **Switch to the target branch** (e.g., `main`):
   - Go to **Git Branches** in the bottom-right corner.
   - Select the branch you want to merge **into** and click **Checkout**.

2. **Merge another branch**:
   - Go to **VCS > Git > Merge Changes**.
   - Select the branch you want to merge **from** (e.g., `feature-branch`).
   - Click **Merge**.

3. **Resolve conflicts** (if any):
   - Android Studio will prompt you with a merge tool to resolve conflicts.

4. **Push the changes**:
   - Go to **VCS > Git > Push** to update the remote repository.

---

## 🔁 **Rebase in Android Studio**

### Steps:
1. **Switch to your working branch** (e.g., `feature-branch`).

2. **Fetch latest changes**:
   - Go to **VCS > Git > Fetch** to update remote tracking branches.

3. **Rebase onto another branch**:
   - Go to **VCS > Git > Rebase**.
   - In the dialog, choose the branch you want to rebase **onto** (e.g., `main`).
   - Click **Start Rebasing**.

4. **Resolve conflicts**:
   - If conflicts occur, Android Studio will pause and allow you to resolve them.

5. **Continue rebase**:
   - After resolving, go to **VCS > Git > Continue Rebasing**.

6. **Force push if needed**:
   - If the branch was already pushed before rebasing, you’ll need to **force push**.
   - Go to **VCS > Git > Push**, enable **force push**, and confirm.

---

### ⚠️ Important Notes
- **Never rebase shared branches**, as it rewrites history.
- Use **interactive rebase** to squash commits or edit messages:
  - Go to **VCS > Git > Rebase**, set the `Onto` field (e.g., `HEAD~3`), and choose actions like `pick`, `reword`, `edit`, or `squash`.

---


Here's how you can perform **Git Merge** and **Git Rebase** operations in **Xcode**, based on official Apple documentation and community insights:

---

## 🔄 **Merge in Xcode**

Xcode provides a **visual interface** for merging branches.

### ✅ Steps to Merge:
1. **Open Source Control Navigator**:
   - Go to **View > Navigators > Source Control**.

2. **Switch to the Target Branch**:
   - Expand your repository and the **Branches** folder.
   - Control-click the branch you want to merge **into** (e.g., `main`) and choose **Switch**.

3. **Merge the Source Branch**:
   - Control-click the branch you want to merge **from** (e.g., `feature-branch`) and choose:
     ```
     Merge 'feature-branch' into 'main'
     ```

4. **Resolve Conflicts (if any)**:
   - Xcode will show a comparison view.
   - You can choose:
     - **Left**
     - **Right**
     - **Left Then Right**
     - **Right Then Left**
   - Click **Merge** to complete the process[1](https://developer.apple.com/documentation/xcode/combining-code-changes-in-a-source-control-repository).

---

## 🔁 **Rebase in Xcode**

Xcode does **not natively support full Git rebase** via its UI, but you can perform a limited rebase during a **pull operation**.

### ✅ Steps to Rebase:
1. **Checkout the Branch You Want to Rebase**:
   - Use the Source Control navigator to switch to your working branch.

2. **Pull with Rebase Option**:
   - Go to **Source Control > Pull**.
   - In the dialog, select the branch you want to rebase **onto**.
   - Check the box:
     ```
     Rebase local changes onto upstream changes
     ```
   - Click **Pull** to rebase your branch[2](https://stackoverflow.com/questions/8218233/is-there-support-for-git-rebasing-in-xcode).

3. **Resolve Conflicts Manually**:
   - If conflicts occur, you’ll need to manually edit the files and remove conflict markers.

---

## 🧠 Tips

- For full rebase control (e.g., interactive rebase), use the **Terminal** inside Xcode:
  ```bash
  git checkout feature-branch
  git rebase main
  ```

- You can also use GUI Git tools like **Sourcetree** or **GitKraken** for more advanced operations.

---

Here's how you can perform **Git Rebase** and **Merge** operations using **SourceTree**, a popular Git GUI tool:

---

## 🔁 Rebase in SourceTree

Rebasing helps you **reapply commits** from one branch onto another, creating a cleaner, linear history.

### ✅ Basic Rebase Steps:
1. **Open your repository** in SourceTree.
2. **Checkout the branch** you want to rebase (e.g., `feature-branch`).
3. Click the **Rebase** button in the toolbar.
4. In the dialog:
   - **Source Branch**: the branch you want to rebase **onto** (e.g., `main`).
   - **Target Branch**: your current branch.
5. Click **Rebase** to start the process.
6. Resolve any conflicts if prompted, then continue the rebase[1](https://hatchjs.com/how-to-rebase-in-sourcetree/).

---

### ✨ Interactive Rebase (Advanced)

Use this to **edit, squash, delete, or reorder commits** before merging or pushing:

1. Right-click on a commit and choose:
   ```
   Rebase children of <commit> interactively
   ```
   or go to **Repository > Interactive Rebase**.
2. Use the UI to:
   - **Squash** commits
   - **Edit** commit contents
   - **Reword** messages
   - **Delete** or **reorder** commits
3. Confirm and complete the rebase[2](https://www.atlassian.com/blog/sourcetree/interactive-rebase-sourcetree).

---

## 🔄 Merge in SourceTree

Merging combines changes from one branch into another, preserving full history.

### ✅ Merge Steps:
1. **Checkout the target branch** (e.g., `main`).
2. Click the **Merge** button.
3. Select the branch you want to merge **from** (e.g., `feature-branch`).
4. Optionally check:
   ```
   Create a commit even if merge resolved via fast-forward
   ```
5. Click **OK** to complete the merge[3](https://confluence.atlassian.com/get-started-with-sourcetree/merge-changes-from-one-branch-to-another-git-847359121.html).

---

### 🧠 Tips

- **Rebase** is ideal for cleaning up history before merging.
- **Merge** is safer for collaborative workflows.
- Avoid rebasing **shared branches** unless coordinated with your team.

---

In **SourceTree**, a Git GUI client, the merge options you mentioned control how merges are handled when integrating changes from one branch into another. Here's what each option means:
<img width="596" height="282" alt="image" src="https://github.com/user-attachments/assets/0653a635-7356-4e24-a9d3-843230dbd5fd" />

---

### 1. **Commit Merged Changes Immediately**
- **Meaning**: Automatically creates a merge commit right after the merge is performed.
- **Use Case**: Useful when you want to finalize the merge without reviewing or modifying the merge commit manually.

---

### 2. **Include Messages from Commits Being Merged in Merge Commit**
- **Meaning**: The merge commit message will include the commit messages from the branch being merged.
- **Use Case**: Helps preserve context and history in the merge commit, especially useful for tracking what changes were introduced.

---

### 3. **Create New Commit Even If Fast-Forward Merge**
- **Meaning**: Forces a merge commit even when a fast-forward is possible.
- **Fast-forward**: Happens when the target branch has no new commits since the source branch diverged, so Git can just move the pointer forward.
- **Use Case**: Maintains a clear history of merges, which can be useful for audit trails or understanding when branches were integrated.

---

### 4. **Rebase Instead of Merge**
- **Meaning**: Rewrites the commit history by placing your changes on top of the target branch, rather than creating a merge commit.
- **Use Case**: Keeps history linear and clean, but can be risky if used on shared branches due to rewriting history.

---

\

