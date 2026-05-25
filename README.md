# Git & GitHub Essentials

This guide covers the core workflow of initializing a local directory, 
managing files, making commits, and pushing your work to GitHub using the **GitHub CLI (`gh`)** 
for authentication and remote creation, alongside explicit **Git remote** commands.

---

## 1. Prerequisites & Installation

1. **Git:** Download and install from [git-scm.com](https://git-scm.com/).
2. **GitHub Account:** Sign up for a free account at [github.com](https://github.com/).
   * Probably the most important step on GitHub
   * Your professional persona for sharing your work (can also create a free website)
   * Try to use some form of your name -- without any numbers 
		* Good Github usename: my.name or name.my, etc.
		* Bad Github username: NoobMaster69
3. **GitHub CLI (`gh`):**
   * **Windows:** Download and run the official `.msi` installer from [cli.github.com](https://cli.github.com/).
   * **macOS:** Download the standalone application zip directly from [cli.github.com](https://cli.github.com/). 
     * Unzip the file in Finder.
     * Open your terminal and run the following command to move the executable into your execution path:
       ```bash
       sudo mv ~/Downloads/gh_*/bin/gh /usr/local/bin/
       ```
     * Verify the installation by checking the version:
       ```bash
       gh --version
       ```

---

## 2. Authenticate with GitHub CLI (`gh`)

Instead of manually generating Personal Access Tokens (PATs) or managing SSH keys, 
authenticate your entire machine using a simple browser handshake.

Run the following command:
* At the command line enter:
```gh auth login```
* Follow the prompts to authenticate via HTTPS and web browser
## 3. Configure Global Identity (use your guthub username and email)
Before creating your first repository, tell Git who you are so your commits are properly attributed.
### Set your global username
git config --global user.name "Your Name"

### Set your global email address (use your GitHub-associated email)
git config --global user.email "your.email@example.com"

**Note: It is extremely import not to try to set up two github accounts**

## 4. Create a local project/files
Use standard terminal commands to navigate, create a project folder, and generate starter files.
### Check where you currently are in the file system
pwd

### Create a new project directory
mkdir [repo-name]

### Move into your new directory
cd [repo-name]

# Create an empty sample file
touch sample-file.txt

# Create a file with markdown text directly from the command line
echo "# Git/Github Basics Repository" > README.md

## 5. Initial Git & Track files
Turn your ordinary directory into a Git-tracked repository and prepare your files for a commit.

### Initialize the repository
git init

### Check the status of your project files (they will appear as untracked/red)
git status

### Add all files in the current folder to the staging area
git add . or git add -A

### Verify the changes are staged (they will now appear green)
git status


## 6. Make First Commit
Commit staged files to **local** Git history
### Commit your changes with a descriptive message
git commit -m "Initial commit: Add project files and README"

### See a history and IDs of previous commits
git log 

### You can also undo a commit either unstage the files or revert files to a previous version
```git reset --soft HEAD~1``` (just unstage your commited files)
```git reset --hard HEAD~1``` (any changes to all committed files undone to the previous commit) **use carefully**


## 7. Link and push to Github w/git  & gh
Typically you make a repo on Github website directly. 
However you can also do this from the command line with the utility
gh.

# 1. Create the blank repository on GitHub using the CLI
gh repo create demo-repo --public

# 2. Set the default branch to main locally
git branch -M main

# 3. Explicitly link your local repository to the new GitHub remote
git remote add origin [https://github.com/YOUR_GITHUB_USERNAME/demo-repo.git](https://github.com/YOUR_GITHUB_USERNAME/demo-repo.git)

# 4. Push your local main branch up to the remote origin
git push -u origin main

## 8. You can consolidate all of the repo creation steps into a single command with uv

# 1. If you don't have uv first run pip install uv at the command line
# 2. Initial a git repo with the command uv init demo-repo
  * creates the repo, including a Python virtual environment, README.md, pyproject.toml and .gitignore
# 3. Connect your repo to github using one of the methods above  