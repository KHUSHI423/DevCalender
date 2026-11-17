# Git and GitHub for Beginners — Complete Notes

> Based on the transcript **“Git and GitHub for Beginners - Crash Course”**.  
> These notes follow the concepts and workflow demonstrated in the video, with commands grouped for quick practice.

## 1. What is Git?

- **Git** is a free, open-source **version control system (VCS)**.
- It tracks changes made to source code over time.
- Developers can:
  - See what changed and when.
  - Understand the history of a project.
  - Identify when bugs were introduced.
  - Return to an earlier version when required.
  - Work on separate features without disturbing the main code.

### What is version control?

1. Save the initial version of the code.
2. Make changes to the code.
3. Save those changes as another version.
4. Repeat as the project evolves.
5. Inspect or restore earlier versions when needed.

## 2. Git vs GitHub

| Git | GitHub |
|---|---|
| Version control tool | Online platform for hosting Git repositories |
| Tracks changes locally | Stores and displays remote repositories |
| Works through terminal or GUI tools | Supports collaboration, code review and project portfolios |
| Can be used without GitHub | Uses Git to manage repository history |

Other remote-hosting alternatives mentioned in the video include **Bitbucket** and **GitLab**.

## 3. Important terminology

| Term | Meaning |

| Directory               | A folder on your computer |
| Terminal / Command Line | Interface where you type commands to navigate files, run programs and perform operations |
| CLI               | Command Line Interface |
| Code editor       | Application designed for writing and editing code |
| Repository / Repo | Project folder managed by Git, containing project files and history |
| Local repository  | Repository stored on your computer |
| Remote repository | Repository hosted somewhere else, such as GitHub |
| Commit            | A saved snapshot of changes in Git |
| Branch            | An independent line of development |
| Merge             | Combining changes from one branch into another |
| Fork              | Your own GitHub copy of another user's repository |
| Pull request (PR) | Request to merge changes from one branch/repository into another |
| Clone             | Copying a remote repository to your local machine |
| Push              | Sending local commits to a remote repository |
| Pull              | Fetching and integrating remote changes into the local branch |
| Staging           | Selecting changes to include in the next commit |
| Diff              | A comparison showing changes between versions |

### Basic terminal commands

```bash
pwd                 # Show current directory
ls                  # List files and folders
ls -la              # List all files, including hidden ones
cd folder-name      # Move into a folder
cd ..               # Move to parent folder
```

- `cd` means **change directory**.
- `ls -la` is useful for viewing hidden files such as `.git`.
- The video also demonstrates `la` as a shell shortcut on the presenter's Mac; `ls -la` is the more portable command.

## 4. Main Git commands — overview

| Command | Purpose |
|---|---|
| `git clone` | Download an existing remote repository |
| `git init` | Turn the current folder into a Git repository |
| `git status` | Show changed, staged and untracked files |
| `git add` | Stage changes for the next commit |
| `git commit` | Save staged changes in Git history |
| `git push` | Upload local commits to a remote |
| `git pull` | Bring remote changes into the local branch |
| `git branch` | List branches |
| `git checkout` | Switch branches or create a branch with `-b` |
| `git merge` | Merge another branch into the current branch |
| `git diff` | Inspect differences |
| `git remote -v` | Show configured remote repositories |
| `git reset` | Unstage changes or move the current branch pointer |
| `git log` | View commit history |

**Remember the basic local workflow:**

```text
Edit files
   ↓
git status
   ↓
git add
   ↓
git commit
   ↓
git push
```

## 5. GitHub repositories and README

### Creating a repository on GitHub

1. Create/sign in to a GitHub account and verify the account.
2. Select **New repository** from the dashboard or the plus menu.
3. Enter a repository name.
4. Choose the required settings and create the repository.
5. A repository contains the files and folders for a project.

### README.md

- A README is commonly used to describe a project.
- It can explain:
  - What the project does.
  - How to use or run it.
  - Setup instructions.
  - Other relevant project information.
- `.md` means **Markdown**, a lightweight text-formatting syntax.
- GitHub displays a repository's `README.md` prominently by default.

Example:

```markdown
# Demo Project

A short description of the project.

## Features

- Feature one
- Feature two

## Setup

Instructions for running the project.
```

Common Markdown:
- `# Heading 1`
- `## Heading 2`
- `- List item`
- `**bold text**`
- `` `inline code` ``

### Commits through the GitHub website

- You can create or edit files directly in GitHub's online interface.
- When you commit through the GitHub interface, GitHub handles staging and committing for you.
- The changes are already on the remote repository, so a separate `git push` is not needed for those web edits.
- The commit message records what was saved.

### Viewing commit history

- Open the repository's **Commits** view.
- Each commit has a unique identifier (hash) and a message.
- A commit diff shows:
  - Green lines with `+`: added lines.
  - Red lines with `-`: removed lines.
  - Unchanged lines: context that remained the same.

## 6. Installing and setting up Git

### Check whether Git is installed

```bash
git --version
```

- The video notes that Git is commonly already available on macOS and Linux.
- On Windows, install Git and consider selecting **Git Bash** during installation, as demonstrated.
- On macOS, the video recommends using the Homebrew package manager where appropriate.
- Installation steps can vary by operating system.

### Code editor

- The video uses **Visual Studio Code (VS Code)**.
- VS Code is a free code editor available for Windows, macOS and Linux.
- Open a project folder in VS Code.
- Open its integrated terminal through **View → Terminal**.
- The terminal starts in the opened folder, making it convenient to run Git commands there.

## 7. Clone a GitHub repository to your computer

Use `git clone` when a repository already exists remotely and you want a local copy.

```bash
git clone <repository-url>
cd <repository-folder>
```

Steps:
1. Open the repository on GitHub.
2. Copy its clone URL (the video demonstrates SSH).
3. Open a terminal in the parent directory where you want the project.
4. Run `git clone <repository-url>`.
5. Enter the newly created repository folder with `cd`.

### The hidden `.git` directory

- A cloned repository contains a hidden `.git` directory.
- It stores Git's repository data, including commit history and other information needed to manage versions.
- It is usually hidden in normal file views.
- Use the following command to see hidden files:

```bash
ls -la
```

**Important:** `.git` is what makes the project folder a Git repository. Do not casually delete it.

## 8. Understanding the working tree, staging area and commits

Git does not automatically include every file change in a commit. You select changes to stage first.

### Three important areas

1. **Working directory:** Files you are currently editing.
2. **Staging area (index):** Changes selected for the next commit using `git add`.
3. **Repository history:** Changes saved as commits using `git commit`.

```text
Working Directory
       |
       | git add
       v
Staging Area
       |
       | git commit
       v
Local Git Repository
       |
       | git push
       v
Remote Repository (GitHub)
```

### Check file status

```bash
git status
```

It helps identify:
- Modified files.
- Untracked files.
- Staged changes ready to commit.
- Whether there is anything left to commit.

### Stage changes

Stage all changes in the current directory:

```bash
git add .
```

Stage only a particular file:

```bash
git add README.md
```

- `.` means all applicable changes in the current directory and its subdirectories.
- You can stage individual files when you do not want every change included.

### Commit changes

```bash
git commit -m "Add index HTML file"
```

- `-m` supplies the commit message.
- A commit message should describe what changed and, where useful, why.
- The video also demonstrates a second `-m` for a longer commit description:

```bash
git commit -m "Add index HTML file" -m "Create the initial HTML page"
```

A commit saves changes in the **local Git history**. It does not automatically upload them to GitHub.

### Push changes

```bash
git push
```

Or explicitly specify the remote and branch:

```bash
git push origin master
```

- `origin` is the conventional name for the remote repository.
- `master` is the branch being pushed in the video examples.
- A push uploads committed local changes to the remote repository.

## 9. Connecting your local machine to GitHub using SSH

The video demonstrates SSH key authentication so the local Git client can authenticate with GitHub.

### Public key vs private key

| Public key | Private key |
|---|---|
| Commonly has `.pub` extension | Does not have `.pub` extension |
| Added to your GitHub account | Kept securely on your local machine |
| Can be shared with GitHub | Must never be shared |
| Used by GitHub to verify the matching private key | Used locally to prove possession of the key |

**Security rule:** Never upload, publish or send your private SSH key. Only add the public key to GitHub.

### General setup flow shown in the video

1. Generate an SSH key pair using `ssh-keygen`.
2. Choose the key type and strength as required by the setup.
3. Enter the email associated with your GitHub account when prompted in the demonstrated command.
4. Choose the key file location/name.
5. Optionally set a passphrase.
6. Locate the generated public key file (`.pub`).
7. Copy the complete public key.
8. In GitHub, open **Settings → SSH and GPG keys → New SSH key**.
9. Give the key a descriptive title and paste the public key.
10. Start/configure the SSH agent and add the key locally as required by your operating system.

The video refers to commands such as:

```bash
ssh-keygen
ssh-add <path-to-private-key>
```

It also demonstrates copying a public key with `pbcopy` on macOS:

```bash
pbcopy < <path-to-public-key.pub>
```

`pbcopy` is macOS-specific; use the appropriate clipboard method for your operating system.

The video also mentions configuring the SSH agent and, for the environment discussed, adding the key location/configuration to the SSH config file. Exact setup details can vary by OS and SSH configuration.

## 10. Push an existing local repository to GitHub

There are two starting situations:

- **Situation A:** You created the repository on GitHub and cloned it locally.
- **Situation B:** You created a project folder locally first and initialized Git there.

For Situation A, the clone already configures the remote, so you can normally push to it.

### Initialize a repository locally

```bash
cd <project-folder>
git init
```

- `git init` creates the Git repository metadata in the current folder.
- The `.git` directory is created.
- You can now use Git commands in that folder.

Example first commit:

```bash
git status
git add .
git commit -m "Create initial README"
```

### Why `git push origin master` may fail

If you initialized the repository locally, it may not yet know about a remote repository. A push can fail because `origin` has not been configured.

### Add a remote repository

1. Create an empty repository on GitHub.
2. Copy its remote URL.
3. Connect the local repository to it:

```bash
git remote add origin <repository-url>
```

4. Verify the remote:

```bash
git remote -v
```

5. Push the branch and set its upstream:

```bash
git push -u origin master
```

- `git remote add` adds a remote reference.
- `origin` is the conventional remote name.
- `-u` sets the upstream tracking relationship.
- Once the upstream is set, future pushes from that branch can usually use:

```bash
git push
```

The same upstream idea is used later for a newly created feature branch.

## 11. Local Git workflow vs GitHub web workflow

| Work through GitHub website | Work locally |
|---|---|
| Edit/create files in GitHub | Edit/create files in a local editor |
| Commit through GitHub interface | `git add` to stage |
| GitHub handles staging | `git commit` to save locally |
| Changes are already on GitHub | `git push` to upload to GitHub |
| No separate push for web edits | Push is needed to update the remote |

A pull request may be required when:
- You do not have direct permission to change the target repository/branch.
- The project requires code review before merging.
- You are contributing to another person's project.

## 12. Branching

### What is a branch?

- A branch is a separate line of development within a repository.
- The video uses `master` as the main/default branch.
- New branches initially point to the same project state as the branch from which they were created.
- Commits made on one branch do not automatically appear on another branch.
- Branches let developers work on features, bug fixes or experiments without immediately changing the main branch.

### Why use branches?

- Build unfinished features safely.
- Avoid introducing unstable code into the main branch.
- Work on multiple tasks independently.
- Allow multiple developers to work in parallel.
- Create a hotfix branch to fix an urgent issue while feature development continues.

### List branches

```bash
git branch
```

- The `*` marks the currently active branch.

### Create and switch to a new branch

```bash
git checkout -b feature-readme-instructions
```

This:
- Creates a branch.
- Switches the working directory to that branch.

### Switch branches

```bash
git checkout master
git checkout feature-readme-instructions
```

The video demonstrates using **Tab** for terminal auto-completion of branch names.

### Branch naming

Use meaningful names that communicate the task. Examples from the workflow:

```text
feature-readme-instructions
feature/issue-11
bugfix-login-error
hotfix-payment-error
```

The exact naming convention depends on the team/project.

### Commit changes on a feature branch

```bash
git status
git add README.md
git commit -m "Update README instructions"
```

These commits belong to the current branch. Switching to `master` will not show those changes until the branch is merged.

## 13. Git diff

`git diff` compares changes and helps you review what will be changed.

```bash
git diff
```

- Shows changes in the working directory that are not staged.
- Added lines are shown with `+`.
- Removed lines are shown with `-`.

Compare the current branch with another branch:

```bash
git diff master
```

The video uses this before merging to inspect what is different.

When the output opens in a pager, press `q` to exit.

## 14. Push a feature branch and create a pull request

### Push a new branch

```bash
git push -u origin feature-readme-instructions
```

- The first push of a new branch commonly needs the upstream to be set.
- After that, `git push` can usually be used from the same branch.

### What is a pull request?

A **pull request (PR)** asks for changes from one branch to be reviewed and merged into another branch.

Example:

```text
feature-readme-instructions  →  master
          source                  base
```

### Pull request workflow

1. Create a feature branch.
2. Make changes.
3. Stage and commit the changes.
4. Push the feature branch to GitHub.
5. Open GitHub; it may detect the new branch and suggest creating a PR.
6. Select the **base** branch (the branch receiving changes).
7. Select the **compare/source** branch (the branch containing your changes).
8. Add a useful PR title and description.
9. Create the PR.
10. Review the changed files and diffs.
11. Team members can comment on the PR or specific lines.
12. Make requested changes locally, commit them and push them to the same branch; the PR updates.
13. Merge the PR when it is ready and approved.

### Base vs compare branch

- **Base:** Where the changes will be merged.
- **Compare:** The branch containing the changes being proposed.

Always check the direction before creating a PR.

### Reviewing code in a PR

The PR interface can show:
- Comments and discussion.
- Commits included in the PR.
- Files changed.
- Added and removed lines (diff).
- Comments attached to specific lines of code.

The video demonstrates adding a line-specific comment and then merging the PR.

## 15. Pull remote changes to your local machine

After a PR is merged on GitHub, the local branch does not automatically update.

Switch to the target branch and pull:

```bash
git checkout master
git pull
```

If upstream tracking is not configured:

```bash
git pull origin master
```

- `git pull` brings remote changes into the current local branch.
- Pull the latest main-branch changes before continuing work when appropriate.
- The video then deletes the feature branch after it has been merged.

### Delete a local branch

```bash
git branch -d feature-readme-instructions
```

- `-d` deletes a branch that Git considers safely merged.
- The video recommends cleaning up temporary feature branches after merging.
- Long-lived branches such as `dev`, `staging` and `master` are treated differently and are generally retained.

## 16. Merge branches locally

A branch can also be merged locally.

Typical sequence:

```bash
git checkout master
git merge feature-readme-instructions
```

This merges the named branch into the **current branch**.

The video notes that, in the demonstrated collaborative workflow, feature branches are commonly pushed and merged through a pull request. It also shows merging the latest main branch into a feature branch to keep it up to date.

### Keep a feature branch up to date

1. Pull the latest changes into the local main branch.
2. Switch to your feature branch.
3. Merge the main branch into the feature branch.

```bash
git checkout master
git pull
git checkout feature-branch
git merge master
```

This helps avoid letting the feature branch fall too far behind the main branch.

## 17. Merge conflicts

### What is a merge conflict?

A merge conflict occurs when Git cannot automatically combine changes. A common example is when two branches modify the same part of the same file differently.

Git cannot decide which version should be kept, so a developer must resolve the conflict.

### Conflict markers

A conflicted file may contain markers like:

```text
<<<<<<< HEAD
Code from the current branch
=======
Code from the branch being merged
>>>>>>> branch-name
```

Meaning:
- `<<<<<<< HEAD`: Start of the current branch's conflicting section.
- `=======`: Separates the two versions.
- `>>>>>>> branch-name`: End of the incoming branch's section.

### How to resolve a conflict

1. Open the conflicted file in your code editor.
2. Compare the current and incoming changes.
3. Decide which code should remain:
   - Keep current change.
   - Keep incoming change.
   - Combine both.
   - Write a corrected version.
4. Remove all conflict markers.
5. Save the file.
6. Stage the resolved file.
7. Commit the resolution.

Example:

```bash
git status
# Edit the conflicted file and remove conflict markers
git add index.html
git commit -m "Resolve merge conflict"
```

The video also demonstrates editor buttons such as:
- Accept Current Change.
- Accept Incoming Change.
- Accept Both Changes.

**Important:** Do not blindly accept one side. Understand the intended behavior and verify the final code.

## 18. `git commit -a` / `git commit -am`

The video demonstrates a shortcut for committing changes to files that Git already tracks:

```bash
git commit -am "Update existing file"
```

- `-a` stages modifications and deletions of already tracked files.
- `-m` supplies the commit message.
- This shortcut does **not** include new/untracked files.
- New files must first be staged with `git add`.

Use the normal workflow when unsure:

```bash
git add .
git commit -m "Describe the changes"
```

## 19. Undoing staging and commits with `git reset`

The video demonstrates `git reset` for removing files from the staging area and moving the current branch pointer to an earlier commit.

### Unstage changes

If a file was staged accidentally:

```bash
git reset
```

Or unstage a particular file:

```bash
git reset README.md
```

- The changes remain in the working directory.
- They are simply removed from the staging area.

### Undo the most recent commit but keep the changes

```bash
git reset HEAD~1
```

- `HEAD` points to the current/latest commit.
- `HEAD~1` means the commit one step before the current commit.
- With the default mixed reset behavior shown in the video, the latest commit is removed from the current branch history and its changes are left unstaged in the working directory.

### Reset to a particular commit

```bash
git log
git reset <commit-hash>
```

- `git log` displays commit history in reverse chronological order.
- Each commit has a unique hash.
- Resetting to a selected commit moves the current branch pointer to that commit.
- With the default mixed behavior, later changes are kept in the working tree but unstaged.

### Hard reset — discard later changes

```bash
git reset --hard <commit-hash>
```

- Moves the current branch pointer to the selected commit.
- Resets the staging area and working tree to match that commit.
- Changes after that commit are discarded from the working tree.
- This can permanently remove uncommitted work.

<aside>
**Caution:** `git reset --hard` is destructive. Check `git status`, inspect the target commit, and make a backup or branch if there is any chance you may need the work. Be especially careful when rewriting history that has already been shared with others.
</aside>

### `HEAD` in simple terms

- `HEAD` is Git's reference to the current checked-out commit/branch position.
- `HEAD~1` refers to its first parent (one commit earlier in the simple linear history shown in the video).

### View commit history

```bash
git log
```

Good commit messages make the history easier for people to understand.

## 20. Forking another person's repository

### What is a fork?

- A fork is a copy of another GitHub repository under your own GitHub account.
- It is useful when you do not have permission to directly modify the original repository.
- You can freely make changes in your fork, subject to the repository's license and applicable rules.
- A fork gives you a separate place to experiment and prepare contributions.

### Fork-based contribution workflow

```text
Original Repository
        |
        | Fork on GitHub
        v
Your GitHub Fork
        |
        | git clone
        v
Your Local Machine
        |
        | edit → add → commit
        v
Your Local Fork
        |
        | git push
        v
Your GitHub Fork
        |
        | Pull Request
        v
Original Repository
```

Steps:
1. Open another person's repository on GitHub.
2. Click **Fork**.
3. Choose your GitHub account as the destination.
4. Wait for GitHub to create the copy.
5. Clone your fork to your computer.
6. Create branches and make changes.
7. Commit and push the changes to your fork.
8. Create a pull request from your fork/branch to the original repository.
9. The original maintainers can review and decide whether to merge it.

### Pull request from a fork

- **Base repository/branch:** Original repository and the branch you want to contribute to.
- **Head/source repository/branch:** Your fork and the branch containing your changes.
- The PR displays the differences and commits being proposed.

The video demonstrates editing a README in a fork, committing it to a `dev` branch, and creating a PR to the original repository.

## 21. Main, development and staging branches

The video explains that larger projects may keep long-lived branches for different purposes.

| Branch | Role described in the video |
|---|---|
| `master` | Main/default branch in the examples |
| `dev` | Integration branch where feature work may be combined |
| `staging` | May be reserved for a staging environment/workflow |

A possible workflow described:

1. Developers create temporary feature or bug-fix branches.
2. They merge those branches into `dev`.
3. Temporary branches are deleted after merging.
4. When development changes are ready, `dev` is merged into `master`.
5. Long-lived branches such as `dev` and `master` remain.

The exact branch strategy differs across teams and repositories. The transcript uses `master`; repositories may use another default branch name.

## 22. Useful command reference

### Setup and repository creation

```bash
git --version
git init
git clone <repository-url>
```

### Inspect repository and changes

```bash
git status
git branch
git log
git diff
git diff <branch-name>
git remote -v
```

### Stage and commit

```bash
git add .
git add <file-name>
git commit -m "Commit message"
git commit -m "Title" -m "Description"
git commit -am "Commit tracked-file changes"
```

### Remote operations

```bash
git remote add origin <repository-url>
git push origin master
git push -u origin master
git push
git pull origin master
git pull
```

### Branch operations

```bash
git branch
git checkout <branch-name>
git checkout -b <new-branch-name>
git merge <branch-name>
git branch -d <branch-name>
```

### Undo operations

```bash
git reset
git reset <file-name>
git reset HEAD~1
git reset <commit-hash>
git reset --hard <commit-hash>
```

## 23. Two complete workflows to remember

### A. Starting from a GitHub repository

```bash
# 1. Download the repository
git clone <repository-url>

# 2. Enter the repository
cd <repository-folder>

# 3. Check current state
git status

# 4. Edit files, then stage changes
git add .

# 5. Save a commit
git commit -m "Describe the change"

# 6. Upload commits
git push
```

### B. Starting from a local project folder

```bash
# 1. Enter the project
cd <project-folder>

# 2. Initialize Git
git init

# 3. Stage and commit
git add .
git commit -m "Initial commit"

# 4. Create an empty GitHub repository first,
#    then connect it as origin
git remote add origin <repository-url>

# 5. Push and set upstream
git push -u origin master
```

### C. Contributing a feature through a pull request

```bash
# 1. Start from an updated main branch
git checkout master
git pull

# 2. Create a feature branch
git checkout -b feature-new-functionality

# 3. Make changes, then stage and commit
git status
git add .
git commit -m "Add new functionality"

# 4. Push the feature branch
git push -u origin feature-new-functionality

# 5. Open a PR on GitHub:
#    feature-new-functionality → master

# 6. After the PR is merged, update local master
git checkout master
git pull

# 7. Delete the merged local feature branch
git branch -d feature-new-functionality
```

## 24. Common mistakes and what they mean

| Situation | Meaning / next step |
|---|---|
| `git push` says no upstream is configured | Set the upstream on the first push, e.g. `git push -u origin <branch>` |
| `origin` does not appear to be a Git repository | Check whether the remote was added with `git remote add origin <URL>` |
| A new file does not appear in a commit | Stage it with `git add <file>` |
| Commit exists locally but not on GitHub | Push it with `git push` |
| Changes on a feature branch are missing on master | They have not been merged into master yet |
| Local master does not show a PR merge | Switch to master and run `git pull` |
| Git refuses to switch branches because local changes would be overwritten | Commit or otherwise safely preserve the changes before switching; the video briefly mentions `git stash` as a temporary holding area |
| Merge conflict appears | Edit the file, resolve the content, remove conflict markers, stage and commit |
| Accidentally staged a file | Use `git reset <file>` to unstage it while keeping the edits |
| Need to inspect what changed | Use `git status` and `git diff` |

## 25. Key concepts — quick differences

### Clone vs Pull

| Clone | Pull |
|---|---|
| Gets a repository onto your machine for the first time | Updates an existing local repository |
| Usually used once per local copy | Used repeatedly to bring remote changes in |

### Add vs Commit vs Push

| Command | What it does |
|---|---|
| `git add` | Selects changes for the next commit |
| `git commit` | Saves staged changes in local Git history |
| `git push` | Uploads local commits to the remote repository |

### Branch vs Fork

| Branch | Fork |
|---|---|
| Separate line of development within a repository | Separate GitHub copy of a repository |
| Commonly used by collaborators with repository access | Commonly used to contribute to repositories you do not own |
| Shares the repository itself | Lives under a different GitHub account/namespace |

### Merge vs Pull request

| Merge | Pull request |
|---|---|
| Git operation that combines branch histories/changes | Collaboration and review request to merge changes |
| Can be done locally with `git merge` | Created on GitHub in the workflow shown |
| Does not inherently require a review interface | Provides discussion, review and approval workflow |

### Git vs GitHub

- Git manages version history.
- GitHub hosts Git repositories and adds collaboration features such as pull requests and code review.

## 26. Last-minute revision checklist

Make sure you can explain and perform these without looking at the notes:

- [ ] Explain version control and why Git is used.
- [ ] Differentiate Git and GitHub.
- [ ] Explain repository, local repo and remote repo.
- [ ] Check Git installation with `git --version`.
- [ ] Clone a repository and enter its folder.
- [ ] Explain what the hidden `.git` folder stores.
- [ ] Check changes using `git status`.
- [ ] Stage files using `git add`.
- [ ] Commit with a meaningful message.
- [ ] Push commits to GitHub.
- [ ] Explain public and private SSH keys.
- [ ] Initialize a local repository with `git init`.
- [ ] Add and verify a remote using `git remote`.
- [ ] Explain branches and create/switch branches.
- [ ] Compare changes using `git diff`.
- [ ] Push a feature branch and create a PR.
- [ ] Explain base branch vs compare branch.
- [ ] Pull merged changes to the local main branch.
- [ ] Explain and resolve merge conflicts.
- [ ] Unstage changes and understand `git reset`.
- [ ] Explain the risk of `git reset --hard`.
- [ ] Explain forking and the contribution workflow.

## 27. The complete mental model

```text
Git = version control system
GitHub = remote hosting + collaboration

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

Remote Repository
    |
    | git pull
    v
Local Repository

Feature Branch
    |
    | push
    v
GitHub Feature Branch
    |
    | Pull Request + Review
    v
Main / Target Branch
    |
    | pull
    v
Updated Local Main Branch
```

**Most important habit:** Before committing, check `git status`; before merging, inspect the changes; after a PR is merged, pull the updated target branch locally.
