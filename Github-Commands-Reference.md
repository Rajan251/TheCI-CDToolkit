# Ultimate Git/GitHub Master Reference

```diff
+ Legend: [🔹Basic] [🔸Intermediate] [🔺Advanced]
```
### Repository Management

# Repository Management Commands

## Initialization & Cloning
| Command | Example | Explanation |
|---------|---------|-------------|
| `git init` | `git init` | Creates new Git repository in current directory (creates .git folder) |
| `git init <dir>` | `git init my-project` | Creates new Git repo in specified directory |
| `git clone <url>` | `git clone https://github.com/user/repo.git` | Downloads entire repository from remote URL |
| `git clone <url> <dir>` | `git clone https://... project-folder` | Clones repo into specified directory name |

## Configuration
| Command | Example | Explanation |
|---------|---------|-------------|
| `git config --global user.name` | `git config --global user.name "John Doe"` | Sets global username for all commits |
| `git config --global user.email` | `git config --global user.email "john@example.com"` | Sets global email for all commits |
| `git config --list` | `git config --list` | Shows all current Git configurations |

## Repository Inspection
| Command | Example | Explanation |
|---------|---------|-------------|
| `git status` | `git status` | Shows working tree status (staged/unstaged files) |
| `git log` | `git log` | Displays commit history |
| `git log --oneline` | `git log --oneline` | Shows compact commit history |
| `git remote -v` | `git remote -v` | Lists all configured remote repositories |

## Advanced Cloning Options
| Command | Example | Explanation |
|---------|---------|-------------|
| `git clone --depth <n>` | `git clone --depth 1 https://...` | Shallow clone (only last n commits) |
| `git clone --branch <name>` | `git clone --branch dev https://...` | Clones specific branch only |
| `git clone --single-branch` | `git clone --single-branch https://...` | Clones only one branch's history |

## Repository Maintenance
| Command | Example | Explanation |
|---------|---------|-------------|
| `git gc` | `git gc` | Garbage collection (optimizes repository) |
| `git fsck` | `git fsck` | Verifies repository integrity |
| `git count-objects -v` | `git count-objects -v` | Counts unpacked objects and disk usage |

## Working with Remotes
| Command | Example | Explanation |
|---------|---------|-------------|
| `git remote add <name> <url>` | `git remote add upstream https://...` | Adds new remote repository |
| `git remote remove <name>` | `git remote remove upstream` | Removes remote reference |
| `git remote rename <old> <new>` | `git remote rename origin upstream` | Renames remote reference |

## Special Repository Types
| Command | Example | Explanation |
|---------|---------|-------------|
| `git init --bare` | `git init --bare my-repo.git` | Creates bare repository (no working directory) |
| `git clone --mirror` | `git clone --mirror https://...` | Creates exact mirror of remote repo |
| `git bundle create <file>` | `git bundle create repo.bundle HEAD main` | Packages repo into single file |

## Example Workflow
```bash
# Create new repository
mkdir my-project && cd my-project
git init

# Configure user
git config user.name "Developer"
git config user.email "dev@company.com"

# Add remote origin
git remote add origin https://github.com/user/repo.git

# Verify setup
git remote -v
git status
```
