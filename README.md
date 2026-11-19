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
