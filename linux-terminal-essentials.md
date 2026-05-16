# Linux Terminal Essentials

> A beginner-friendly reference for navigating the terminal, managing files, packages, and version control. Perfect for juniors getting started with Linux or ROS development.

---

## Table of Contents

- [Navigation](#navigation)
- [Creating & Managing Files](#creating--managing-files)
- [Reading & Editing Files](#reading--editing-files)
- [Finding Things](#finding-things)
- [Package Management](#package-management-apt)
- [Python Package Management](#python-package-management-pip)
- [Git & Version Control](#git--version-control)
- [Quick Reference Cheat Sheet](#quick-reference-cheat-sheet)

---

## Navigation

```bash
pwd             # Print current directory (where am I right now?)
ls              # List files in current directory
ls -la          # List all files including hidden ones, with details
cd ~/Documents  # Go to the Documents folder
cd ..           # Go up one level
cd ~            # Go back to home directory
```

---

## Creating & Managing Files

```bash
# Directories
mkdir my_project        # Create a folder
mkdir -p a/b/c          # Create nested folders in one shot

# Files
touch hello.py          # Create an empty file
cp hello.py hello2.py   # Copy a file
mv hello2.py renamed.py # Rename or move a file
rm renamed.py           # Delete a file
rm -rf my_project       # Delete a folder and ALL its contents (no undo!)
```

> **Warning:** `rm -rf` is permanent. Double-check your path before running it.

---

## Reading & Editing Files

```bash
cat hello.py    # Print file contents to the terminal
nano hello.py   # Open in Nano (simple, beginner-friendly editor)
code hello.py   # Open in VS Code (requires VS Code to be installed)
```

**Nano quick tips:**
- `Ctrl + O` → Save
- `Ctrl + X` → Exit
- `Ctrl + W` → Search

---

## Finding Things

```bash
find ~ -name "*.py"         # Find all Python files in your home directory
grep -r "import rclpy" .    # Search for text inside files (recursive)
```

---

## Package Management (`apt`)

```bash
sudo apt update                      # Refresh the list of available packages
sudo apt upgrade                     # Upgrade all installed packages
sudo apt install git curl wget       # Install multiple packages at once
sudo apt install python3-pip         # Install pip for Python packages
apt search ros-humble                # Search for ROS packages
apt show python3-pip                 # See details about a specific package
```

> **Tip:** Always run `sudo apt update` before installing anything to get the latest package list.

---

## Python Package Management (`pip`)

```bash
pip3 install numpy            # Install a package
pip3 list                     # List all installed packages
pip3 show numpy               # Show info about a specific package
pip3 install --upgrade numpy  # Upgrade a package to the latest version
```

> **Tip:** Use `pip3` (not `pip`) on most Linux systems to ensure you're using Python 3.

---

## Git & Version Control

Git is how you track changes to your code, collaborate with teammates, and back up your work. If you're new to Git, think of it as a **save system with full history**.

### First-Time Setup

Run these once after installing Git:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global core.editor "nano"       # Use nano as default editor
# git config --global core.editor "code --wait"  # Or use VS Code instead
```

---

### Starting a New Project

```bash
git init my_robot_project   # Create a new repo in a new folder
cd my_robot_project
```

---

### Everyday Workflow

This is the loop you'll repeat constantly:

```bash
git status                        # See what's changed
git add hello.py                  # Stage a specific file
git add .                         # Stage ALL changed files
git commit -m "add hello script"  # Save a snapshot with a message
```

> **Tip:** Write commit messages like "add login feature" or "fix motor speed bug" — not just "update" or "changes".

---

### Viewing History & Differences

```bash
git log --oneline   # See commit history in compact form
git diff            # See what changed since the last commit
```

---

### Cloning an Existing Repo

```bash
git clone https://github.com/some/repo.git  # Download a repo from GitHub
cd repo
```

---

### Working with Branches

Branches let you work on a feature without breaking the main codebase. This is essential for team collaboration.

```bash
git checkout -b feature/my-new-thing   # Create and switch to a new branch
git checkout main                      # Switch back to main branch
git merge feature/my-new-thing         # Merge your branch into current branch
```

**Typical branch workflow:**

```
main ──────────────────────────────────► (stable code)
        └── feature/my-new-thing ──┘
             (your work here)
```

> **Tip:** Always branch off `main` for new features, and merge back only when it's working.

---

## Quick Reference Cheat Sheet

| Task | Command |
|---|---|
| Where am I? | `pwd` |
| List files | `ls -la` |
| Go home | `cd ~` |
| Create folder | `mkdir folder_name` |
| Delete folder *(careful!)* | `rm -rf folder_name` |
| Find a file | `find ~ -name "filename"` |
| Search inside files | `grep -r "text" .` |
| Install a package | `sudo apt install pkg` |
| Install Python lib | `pip3 install lib` |
| Initialize a repo | `git init` |
| Stage & commit | `git add . && git commit -m "msg"` |
| See history | `git log --oneline` |
| Create a branch | `git checkout -b branch-name` |
| Clone a repo | `git clone <url>` |

---

*Feel free to open an issue or PR if something is outdated or missing!*
