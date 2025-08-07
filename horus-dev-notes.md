# Horus Dev Notes

## How to setup pulling and merging from source of the fork

I'll provide you with the complete git command sequence for setting up and merging changes from the upstream repository. Let me first check your current dev notes to see what you already have:
Read file: horus-dev-notes.md
Perfect! I can see you're documenting this process. Here's the complete git command sequence:

### Initial Setup (One-time only)

Since you already have the upstream remote configured, you can skip this step, but for completeness:

```bash
# Check current remotes (you should see both origin and upstream)
git remote -v

# If upstream is missing, add it:
# git remote add upstream git@github.com:ai-evals-course/recipe-chatbot.git
```

### Regular Workflow to Sync with Upstream

Here's the command sequence you'll use regularly to pull and merge changes from the upstream repository:

```bash
# 1. Fetch the latest changes from upstream (doesn't modify your local branches)
git fetch upstream

# 2. Switch to your main branch
git checkout main

# 3. Merge upstream changes into your local main branch
git merge upstream/main

# 4. Push the updated main branch to your fork
git push origin main
```

### Alternative: Using Rebase (for cleaner history)

```bash
# Steps 1-2 are the same
git fetch upstream
git checkout main

# 3. Rebase your local changes on top of upstream changes
git rebase upstream/main

# 4. Push to your fork (may need force push if you had local commits)
git push origin main
```

### If You Have Local Changes on Main (Advanced)

If you have uncommitted changes or local commits on main:

```bash
# If you have uncommitted changes, stash them first
git stash

# Fetch and merge/rebase as above
git fetch upstream
git merge upstream/main  # or git rebase upstream/main

# Restore your stashed changes
git stash pop

# Push to your fork
git push origin main
```

### Best Practice Workflow

For ongoing development, it's better to work on feature branches:

```bash
# Create and switch to a feature branch
git checkout -b feature/my-new-feature

# Make your changes and commit them
git add .
git commit -m "Add new feature"

# When ready to sync with upstream:
git checkout main
git fetch upstream
git merge upstream/main
git push origin main

# Then merge or rebase your feature branch
git checkout feature/my-new-feature
git merge main  # or git rebase main
```

The key commands you'll use most often are:
1. `git fetch upstream`
2. `git checkout main` 
3. `git merge upstream/main`
4. `git push origin main`

This keeps your fork's main branch in sync with the course repository while preserving your ability to work on separate branches for your own development.