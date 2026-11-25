# Git & GitHub Engineering Journey

A hands-on reference repository for mastering Git version control, branching strategies, Pull Request workflows, and collaborative software engineering.

## Essential Git Workflow Cheat Sheet

### 1. Branching & Feature Development
```bash
git checkout main
git pull origin main
git checkout -b feature/descriptive-topic
```

### 2. Staging, Conventional Commits & History
```bash
git status -sb
git add -p
git commit -m "feat(module): concise summary of change"
git log --oneline --graph --decorate --all
```

### 3. Pull Requests via GitHub CLI (`gh`)
```bash
git push -u origin feature/descriptive-topic
gh pr create --base main --head feature/descriptive-topic --fill
gh pr merge --merge --delete-branch
```

### 4. Recovery & Inspection
```bash
git diff HEAD~1
git reflog
git stash push -m "work in progress"
```

### 5. Interactive Rebase, Bisect & Parallel Worktrees
```bash
# Squash or reorder local commits before opening a PR
git rebase -i origin/main

# Binary-search commit history to isolate a regression
git bisect start
git bisect bad HEAD
git bisect good v1.0.0

# Mount an isolated working tree for hotfixes without stashing current work
git worktree add ../hotfix-branch hotfix/critical-patch
git worktree list
```

### 6. Release Tagging, Cherry-Picking & Repository Hygiene
```bash
# Create an annotated release tag and push it to origin
git tag -a v2.1.0 -m "Release v2.1.0: production telemetry upgrades"
git push origin v2.1.0

# Backport a specific commit onto a maintenance branch with provenance reference
git cherry-pick -x <commit-sha>

# Prune deleted remote-tracking branches and inspect untracked artifacts safely
git fetch --all --prune
git clean -fdn
```

### 7. Blame Archaeology, Range Logs & Portable Patches
```bash
# Trace line-by-line authorship while ignoring whitespace-only formatting changes
git blame -w -L 10,40 src/main.py

# Inspect commits touching a specific function or file path
git log -L :calculate_gpa:app.py

# Export commits as portable ".patch" files and apply them cleanly with authorship intact
git format-patch -1 HEAD --stdout > hotfix.patch
git am < hotfix.patch
```

## Parallel Worktrees & Sparse Checkouts

```bash
# Check out a separate branch in a parallel directory without stashing current work
git worktree add ../hotfix-branch feature/urgent-fix
git worktree list
git worktree remove ../hotfix-branch

# Initialize sparse-checkout in cone mode for large monorepos
git sparse-checkout init --cone
git sparse-checkout set src/core tests/unit
```

### 9. Cryptographic Commit Signing & Non-Destructive Git Notes
```bash
# Sign commits and tags using SSH or GPG keys and verify signatures in history
git commit -S -m "feat(security): enforce cryptographic commit verification"
git log --show-signature -n 3

# Attach audit or CI benchmark metadata to a commit without changing its SHA-1/SHA-256 hash
git notes add -m "CI benchmark: 99.4% accuracy, 0 regressions" HEAD
git notes show HEAD
git log --show-notes -n 2
```

### 10. Pickaxe History Search & Regex Code Grepping
```bash
# Find commits that added or removed occurrences of a specific identifier ("pickaxe" search)
git log -S "compute_cardiometabolic_syndrome_index" --oneline

# Find commits whose diff matches a regular expression pattern
git log -G "def (compute|evaluate)_" --stat

# Fast indexed regex search across tracked files with line numbers and file headings
git grep -n --heading --break "FastAPI"
```





