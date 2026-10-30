# Git & GitHub Complete Notes

A practical guide to Git and GitHub covering essential commands, version control,
branching, merging, remote repositories, collaboration, and DevOps workflows.

## Table of Contents

1. Introduction to Git
2. Introduction to GitHub
3. Git vs GitHub
4. Git Installation
5. Initial Configuration
6. Git Architecture and Workflow
7. Creating a Repository
8. Basic Git Commands
9. Staging and Committing
10. Git Logs and History
11. Branching
12. Merging Branches
13. Merge Conflicts
14. Working with Remote Repositories
15. Cloning a Repository
16. Fetch, Pull, and Push
17. Git Stash
18. Git Reset vs Revert
19. .gitignore
20. GitHub Pull Requests
21. Forking a Repository
22. Git Tags
23. Git Rebase
24. Cherry-Pick
25. HEAD in Git
26. GitHub Actions
27. Git Workflow in DevOps
28. Common Git Errors
29. Git Best Practices
30. Git Interview Revision

---

## 1. Introduction to Git

Git is a distributed version control system used to track changes in files
and manage source code.

### Why do we use Git?

- Track changes in source code.
- Maintain a history of modifications.
- Restore earlier versions of files.
- Create and manage branches.
- Support collaboration between developers.
- Integrate source control into CI/CD pipelines.

### Important Features

- Distributed version control
- Branching and merging
- Commit history
- Local repositories
- Offline development
- Change tracking

---

## 2. Introduction to GitHub

GitHub is a platform for hosting Git repositories and collaborating on projects.

### GitHub Features

- Remote repositories
- Pull Requests
- Issues
- Code reviews
- Project collaboration
- GitHub Actions
- Repository access management
- Documentation using README.md

---

## 3. Git vs GitHub

| Git | GitHub |
|---|---|
| Version control system | Repository hosting platform |
| Installed locally | Primarily accessed online |
| Tracks file changes | Hosts Git repositories remotely |
| Supports local commits | Supports Pull Requests and code reviews |
| Works offline | Requires network access for remote operations |

---

## 4. Git Installation

Check whether Git is installed:

```bash
git --version
```

Install Git on Ubuntu:

```bash
sudo apt update
sudo apt install git -y
```

Verify installation:

```bash
git --version
```

---

## 5. Initial Configuration

Configure your Git username:

```bash
git config --global user.name "Your Name"
```

Configure your email:

```bash
git config --global user.email "your-email@example.com"
```

View all configuration:

```bash
git config --list
```

View the configured username:

```bash
git config user.name
```

View the configured email:

```bash
git config user.email
```

### Configuration Levels

- `--system`: Applies to all users on the system.
- `--global`: Applies to the current operating system user.
- `--local`: Applies only to the current repository.

Example:

```bash
git config --local user.name "Project User"
```

---

## 6. Git Architecture and Workflow

Git uses three important areas:

1. Working Directory
2. Staging Area
3. Local Repository

### Working Directory

The location where you create or modify files.

### Staging Area

The area where you select changes to include in the next commit.

### Local Repository

Stores committed snapshots and repository history.

### Basic Workflow

```text
Working Directory
        |
        | git add
        v
Staging Area
        |
        | git commit
        v
Local Repository
        |
        | git push
        v
Remote Repository (GitHub)
```

---

## 7. Creating a Repository

Create a project directory:

```bash
mkdir git-demo
cd git-demo
```

Initialize Git:

```bash
git init
```

Check repository status:

```bash
git status
```

Create a file:

```bash
echo "Learning Git" > notes.txt
```

Check the status again:

```bash
git status
```

Git now detects the untracked file.

---

## 8. Basic Git Commands

### Check Status

```bash
git status
```

Shows modified, staged, and untracked files.

### Initialize a Repository

```bash
git init
```

Creates a new Git repository.

### Add a File to Staging

```bash
git add notes.txt
```

### Add All Changes

```bash
git add .
```

### Commit Changes

```bash
git commit -m "Add initial notes"
```

### View Git Version

```bash
git --version
```

### View Help

```bash
git help
```

---

## 9. Staging and Committing

A commit records a snapshot of the staged changes.

### Example Workflow

```bash
echo "Git basics" > git.txt
git status
git add git.txt
git status
git commit -m "Add Git basics"
```

### View Unstaged Changes

```bash
git diff
```

### View Staged Changes

```bash
git diff --staged
```

### Remove a File from Staging

```bash
git restore --staged notes.txt
```

This removes the file from the staging area without deleting its working
directory contents.

---

## 10. Git Logs and History

### View Commit History

```bash
git log
```

### Compact Commit History

```bash
git log --oneline
```

### Show Recent Commits

```bash
git log -5 --oneline
```

### Display a Graph of Branches

```bash
git log --oneline --graph --all
```

### Show Changes in a Commit

```bash
git show <commit-id>
```

Replace `<commit-id>` with the actual commit hash.

---

## 11. Branching

A branch allows you to develop changes independently.

### List Branches

```bash
git branch
```

### Create a Branch

```bash
git branch feature-login
```

### Switch to a Branch

```bash
git switch feature-login
```

### Create and Switch to a Branch

```bash
git switch -c feature-login
```

### Rename the Current Branch

```bash
git branch -m main
```

### Delete a Merged Branch

```bash
git branch -d feature-login
```

### Force Delete a Branch

```bash
git branch -D feature-login
```

Use force deletion carefully because it can discard unmerged work.

---

## 12. Merging Branches

Merging integrates changes from one branch into another.

Example:

```bash
git switch main
git merge feature-login
```

This merges `feature-login` into the current `main` branch.

### Merge Types

- Fast-forward merge
- Three-way merge

Always check the branch you are currently on before merging.

```bash
git branch
git status
```

---

## 13. Merge Conflicts

A merge conflict occurs when Git cannot automatically reconcile changes.

### Steps to Resolve a Conflict

1. Run the merge operation.
2. Identify the conflicted files.
3. Open each conflicted file.
4. Review the conflict markers.
5. Edit the file to keep the intended content.
6. Stage the resolved file.
7. Complete the merge commit if required.

Example:

```bash
git status
```

After resolving the file:

```bash
git add conflicted-file.txt
git commit
```

Git conflict markers look like this:

```text
<<<<<<< HEAD
Current branch changes
=======
Incoming branch changes
>>>>>>> feature-branch
```

Remove the markers and keep the correct content before committing.

---

## 14. Working with Remote Repositories

A remote connects your local repository to another repository, such as GitHub.

### Add a Remote

```bash
git remote add origin https://github.com/USERNAME/REPOSITORY.git
```

Replace `USERNAME` and `REPOSITORY` with your actual values.

### View Remotes

```bash
git remote -v
```

### Change the Remote URL

```bash
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
```

### Remove a Remote

```bash
git remote remove origin
```

---

## 15. Cloning a Repository

Cloning downloads a repository and its history to your local system.

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
```

Enter the repository directory:

```bash
cd REPOSITORY
```

Check its status:

```bash
git status
```

---

## 16. Fetch, Pull, and Push

### Git Fetch

Downloads remote updates without integrating them into the current branch.

```bash
git fetch origin
```

### Git Pull

Fetches remote changes and integrates them into the current branch.

```bash
git pull origin main
```

### Git Push

Uploads local commits to a remote repository.

```bash
git push origin main
```

### First Push of a New Branch

```bash
git push -u origin feature-login
```

The `-u` option sets the upstream tracking branch.

### Difference Between Fetch, Pull, and Push

| Command | Purpose |
|---|---|
| `git fetch` | Downloads remote updates |
| `git pull` | Downloads and integrates remote updates |
| `git push` | Uploads local commits |

---

## 17. Git Stash

Git stash temporarily stores changes so you can switch tasks without committing
those changes.

### Save Changes

```bash
git stash
```

### List Stashes

```bash
git stash list
```

### Apply the Latest Stash

```bash
git stash apply
```

### Apply and Remove the Latest Stash

```bash
git stash pop
```

### Delete a Stash

```bash
git stash drop
```

### Delete All Stashes

```bash
git stash clear
```

Use `git stash clear` carefully because it removes all saved stashes.

---

## 18. Git Reset vs Revert

Both commands can help undo changes, but they behave differently.

### Git Reset

Moves the current branch reference to another commit.

```bash
git reset --soft HEAD~1
```

Keeps the changes staged.

```bash
git reset --mixed HEAD~1
```

Keeps the changes in the working directory but unstages them.
This is the default reset mode.

```bash
git reset --hard HEAD~1
```

Resets the index and working directory. Uncommitted changes can be lost.

### Git Revert

Creates a new commit that reverses the changes introduced by an earlier commit.

```bash
git revert <commit-id>
```

### Difference

| Git Reset | Git Revert |
|---|---|
| Moves the branch reference | Creates a new reversing commit |
| Can rewrite local history | Preserves existing commit history |
| Can discard changes with `--hard` | Usually safer for shared history |
| Requires care on shared branches | Suitable for reverting published commits |

Prefer `git revert` when undoing changes that have already been shared with others.

---

## 19. .gitignore

A `.gitignore` file specifies intentionally untracked files that Git should ignore.

Create the file:

```bash
touch .gitignore
```

Example `.gitignore`:

```gitignore
# Dependencies
node_modules/

# Environment variables and secrets
.env
.env.*

# Build output
dist/
build/

# Logs
*.log

# Python cache
__pycache__/
*.pyc

# Editor settings
.vscode/

# Operating system files
.DS_Store
Thumbs.db
```

### Important

`.gitignore` does not automatically stop tracking files that are already tracked.

To stop tracking a file while keeping it locally:

```bash
git rm --cached .env
git commit -m "Stop tracking environment file"
```

Never commit passwords, API keys, private keys, or cloud credentials.

---

## 20. GitHub Pull Requests

A Pull Request (PR) proposes changes from one branch to another.

### Typical Workflow

1. Create a feature branch.
2. Make changes.
3. Commit the changes.
4. Push the branch to GitHub.
5. Open a Pull Request.
6. Request a review.
7. Address review comments.
8. Merge the Pull Request.

Example commands:

```bash
git switch -c feature-documentation
```

After editing files:

```bash
git add .
git commit -m "Update project documentation"
git push -u origin feature-documentation
```

Open GitHub to create the Pull Request.

---

## 21. Forking a Repository

A fork is your own GitHub copy of another user's repository.

### Why Fork?

- Contribute to open-source projects.
- Experiment without changing the original repository.
- Propose improvements through Pull Requests.

### Basic Workflow

1. Fork the repository on GitHub.
2. Clone your fork.
3. Create a feature branch.
4. Make and commit changes.
5. Push your branch.
6. Open a Pull Request.

---

## 22. Git Tags

Tags mark specific points in repository history, commonly software releases.

### Create a Tag

```bash
git tag v1.0.0
```

### Create an Annotated Tag

```bash
git tag -a v1.0.0 -m "Version 1.0.0"
```

### List Tags

```bash
git tag
```

### Push a Specific Tag

```bash
git push origin v1.0.0
```

### Push All Tags

```bash
git push origin --tags
```

---

## 23. Git Rebase

Rebase moves or reapplies commits onto another base commit.

Example:

```bash
git switch feature-login
git rebase main
```

### Merge vs Rebase

| Merge | Rebase |
|---|---|
| Integrates branch histories | Reapplies commits onto a new base |
| Can create a merge commit | Usually creates a linear history |
| Preserves existing commit identities | Rebased commits receive new identities |
| Suitable for shared integration workflows | Useful for cleaning up local branch history |

Avoid rebasing commits that others already depend on unless the team has agreed
on how to handle the history rewrite.

---

## 24. Cherry-Pick

Cherry-pick applies the changes from a specific commit to the current branch.

```bash
git cherry-pick <commit-id>
```

### Common Use Case

You need one specific bug fix from another branch without merging the entire branch.

Check the resulting history:

```bash
git log --oneline
```

---

## 25. HEAD in Git

`HEAD` normally points to the currently checked-out commit or branch.

### Examples

```bash
git show HEAD
```

Shows the current commit.

```bash
git diff HEAD
```

Compares the working directory with the current commit.

```bash
git reset --soft HEAD~1
```

Moves the current branch back one commit while keeping the changes staged.

`HEAD~1` refers to the first parent of the current commit.

---

## 26. GitHub Actions

GitHub Actions is a CI/CD and automation platform integrated with GitHub.

### Common Uses

- Running automated tests.
- Building applications.
- Performing code quality checks.
- Building Docker images.
- Deploying applications.
- Automating repository tasks.

### Important Concepts

- Workflow
- Event
- Job
- Step
- Runner
- Action
- Secrets
- Artifacts

### Basic Workflow Example

Create this file:

`.github/workflows/hello.yml`

```yaml
name: Hello Workflow

on:
  push:
    branches:
      - main
  workflow_dispatch:

jobs:
  hello:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Display message
        run: echo "GitHub Actions is running!"
```

This workflow runs on pushes to `main` and can also be triggered manually.

For production workflows, review and pin third-party actions according to your
organization's security requirements.

---

## 27. Git Workflow in DevOps

Git is commonly used throughout the software delivery lifecycle.

### Typical Workflow

```text
Developer
    |
    v
Write Code
    |
    v
Git Add and Commit
    |
    v
Push to GitHub
    |
    v
CI/CD Pipeline Trigger
    |
    v
Build and Test
    |
    v
Build Docker Image
    |
    v
Deploy Application
    |
    v
Monitor Application
```

### Git with DevOps Tools

| Tool | Example Use |
|---|---|
| Git | Version control |
| GitHub | Repository hosting and collaboration |
| Jenkins | CI/CD automation |
| Docker | Application containerization |
| Terraform | Infrastructure as Code |
| AWS | Cloud infrastructure and deployment |
| GitHub Actions | Repository automation and CI/CD |

The exact workflow depends on the project and team.

---

## 28. Common Git Errors

### Error: Nothing to Commit

Check whether any files have changed:

```bash
git status
```

### Error: Remote Origin Already Exists

Check the configured remote:

```bash
git remote -v
```

Update its URL if necessary:

```bash
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
```

### Error: Failed to Push

Fetch remote changes and review them:

```bash
git fetch origin
git status
```

If the remote contains commits missing locally, integrate them appropriately
before pushing.

### Error: Merge Conflict

Check conflicted files:

```bash
git status
```

Resolve the conflicts, stage the files, and complete the merge.

### Error: Wrong Branch

Check the current branch:

```bash
git branch --show-current
```

Switch to the correct branch:

```bash
git switch main
```

### Error: Accidentally Committed a Secret

1. Revoke or rotate the exposed credential immediately.
2. Remove the secret from the repository.
3. Review access and usage logs.
4. Address the Git history if necessary.

Deleting a secret in a later commit does not remove it from earlier commits.

---

## 29. Git Best Practices

- Write meaningful commit messages.
- Commit small, logical changes.
- Use feature branches for independent tasks.
- Review changes before committing.
- Use Pull Requests for team collaboration.
- Keep `.gitignore` updated.
- Never commit credentials or secrets.
- Pull or fetch remote changes regularly.
- Avoid unnecessary force pushes.
- Prefer `git revert` for undoing published commits.
- Write clear README documentation.
- Protect important branches.
- Review CI/CD workflow permissions.
- Keep repositories organized and understandable.

### Example Commit Messages

```text
Add login page
Fix database connection error
Update AWS deployment documentation
Add Docker configuration
Improve API error handling
```

---

## 30. Git Interview Revision

### Q1. What is Git?

Git is a distributed version control system that tracks changes in files.

### Q2. What is GitHub?

GitHub is a platform for hosting Git repositories and collaborating on code.

### Q3. What is a repository?

A repository stores project files and their version history.

### Q4. What is a commit?

A commit records a snapshot of staged changes.

### Q5. What is a branch?

A branch is a movable reference used to develop changes independently.

### Q6. What is a merge conflict?

A merge conflict occurs when Git cannot automatically reconcile changes.

### Q7. What is the difference between fetch and pull?

Fetch downloads remote updates without integrating them. Pull fetches and
integrates remote updates into the current branch.

### Q8. What is the difference between reset and revert?

Reset moves the branch reference and can rewrite local history. Revert creates
a new commit that reverses an earlier commit.

### Q9. What is a Pull Request?

A Pull Request proposes changes for review and possible integration into another
branch.

### Q10. What is .gitignore?

It specifies intentionally untracked files that Git should ignore.

### Q11. What is Git stash?

Stash temporarily saves working changes so you can work on another task.

### Q12. What is Git rebase?

Rebase reapplies commits onto a new base commit.

### Q13. What is a remote repository?

A remote repository is another copy of a repository, often hosted on GitHub.

### Q14. What is HEAD?

HEAD identifies the currently checked-out commit or branch reference.

### Q15. How is Git used in DevOps?

Git stores version-controlled source code and can trigger CI/CD pipelines for
testing, building, and deploying applications.

---

## Practical Revision Checklist

- [ ] Install Git
- [ ] Configure username and email
- [ ] Initialize a repository
- [ ] Add and commit files
- [ ] Inspect commit history
- [ ] Create and switch branches
- [ ] Merge branches
- [ ] Resolve a merge conflict
- [ ] Connect a local repository to GitHub
- [ ] Clone a repository
- [ ] Fetch, pull, and push changes
- [ ] Use Git stash
- [ ] Understand reset and revert
- [ ] Create a .gitignore file
- [ ] Open a Pull Request
- [ ] Create and push a Git tag
- [ ] Understand rebase and cherry-pick
- [ ] Create a basic GitHub Actions workflow

---

## Learning Goals

This repository is intended to serve as a practical reference for:

- Git and GitHub fundamentals
- Technical interview preparation
- Daily command revision
- Cloud and DevOps learning
- CI/CD workflow understanding

Keep practicing these commands in a test repository before using destructive
operations in important projects.

**Keep Learning. Keep Practicing. Keep Building!**