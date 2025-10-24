# 100 - Fixing bug "foo instead of fixme"

# 1. Prepare for bug fixing

When we first ran the unit test, we were alerted about below bug.

```
F
======================================================================
FAIL: test_foo (tests.test_gilded_rose.GildedRoseTest.test_foo)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/local/opt/code/learning-test-driven-development-gilded-rose-kata/python/tests/test_gilded_rose.py", line 12, in test_foo
    self.assertEqual("fixme", items[0].name)
AssertionError: 'fixme' != 'foo'
- fixme
+ foo


----------------------------------------------------------------------
Ran 1 test in 0.002s

FAILED (failures=1)
```

The test is failing because it expects the item name to be "fixme" but it's actually "foo". This is actually expected behavior for the Gilded Rose Kata!

## What's happening:
This is a test-driven development kata where:
- The test is written first (expecting "fixme")
- The code is supposed to be implemented to make the test pass
- The current code returns "foo" instead of "fixme"

Here is how we are going to fix it using GitFlow instructions.

**NOTE**: You can create a new Git branch while in a virtual environment. The virtual environment only affects your Python package installations and doesn't interfere with Git operations.

```
git status
```

You are currently in the main branch.

### Best Practices for Bug Fix Branches:

Commit your current changes first (if you want to keep them):

```
git add .
git commit -m "Some description of your last changes"
git push
```

Check:

```
git status
```

You'll see:

```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

## Method 1: Local branch creation for bug fixing (Not Recommended)

### Create a new branch locally

```bash
# 1. Ensure you're on the main branch and it's up to date
git checkout main
git pull origin main

# 2. Create and switch to a new branch for the bug fix
git checkout -b bug/2-bug-foo-instead-of-fixme

# 3. Verify you're on the new branch
git branch
# You should see: * bug/2-bug-foo-instead-of-fixme

# 4. Check the status
git status
# Should show: On branch bug/2-bug-foo-instead-of-fixme
```

### Alternative: Create branch first, then switch

```bash
# 1. Create the branch without switching to it
git branch bug/2-bug-foo-instead-of-fixme

# 2. Switch to the new branch
git checkout bug/2-bug-foo-instead-of-fixme

# 3. Verify you're on the correct branch
git status
```

### Push the new branch to remote

```bash
# 1. Push the new branch to the remote repository
git push -u origin bug/2-bug-foo-instead-of-fixme

# 2. Verify the branch was pushed
git branch -vv
# Should show: * bug/2-bug-foo-instead-of-fixme 1234567 [origin/bug/2-bug-foo-instead-of-fixme] Latest commit message
```

### Verify your setup

```bash
# Check current branch
git branch

# Check remote tracking
git branch -vv

# Check status
git status

# You should see:
# On branch bug/2-bug-foo-instead-of-fixme
# Your branch is up to date with 'origin/bug/2-bug-foo-instead-of-fixme'.
# nothing to commit, working tree clean
```

## Method 2: GitHub Issue Creation (Recommended)

On GitHub create a new issue: ```Bug: foo instead of fixme``` of type **Bug**, with the following description.

```
F
======================================================================
FAIL: test_foo (tests.test_gilded_rose.GildedRoseTest.test_foo)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/local/opt/code/learning-test-driven-development-gilded-rose-kata/python/tests/test_gilded_rose.py", line 12, in test_foo
    self.assertEqual("fixme", items[0].name)
AssertionError: 'fixme' != 'foo'
- fixme
+ foo


----------------------------------------------------------------------
Ran 1 test in 0.002s

FAILED (failures=1)
```

In the new issue on GitHub click **Create**.

Choose: ```Create a branch for this issue```.

Modify the proposed name of the new branch (here: ```2-bug-foo-instead-of-fixme```) by adding ```bug/``` in front of it (so now the branch name is ```bug/2-bug-foo-instead-of-fixme```), choose **Main** as branch source (optionally choose ```Checkout locally```, although we will work from our remote repository) and choose **Create Branch**.

Lets use the new branch for the bug.

```
# 1. Run the following commands in your local clone.
git fetch origin
```

You should see something like:

```
From https://github.com/vanHeemstraSystems/learning-test-driven-development-gilded-rose-kata
 * [new branch]      bug/2-bug-foo-instead-of-fixme -> origin/bug/2-bug-foo-instead-of-fixme
```

```
# 2. Checkout the new branch in your local clone.
git checkout bug/2-bug-foo-instead-of-fixme
```

```
# 3. Work on your fix while in the virtual environment
```

See [README.md](./100/README.md)

# If the branch doesn't exist locally, create it and track the remote
git checkout -b bug/2-bug-foo-instead-of-fixme origin/bug/2-bug-foo-instead-of-fixme
```
# 4. When done, commit and push:
git add .
git commit -m "Fix: Change item name from 'foo' to 'fixme'"
git push origin bug/2-bug-foo-instead-of-fixme
```

## 6. Create a Pull Request on GitHub

### Step 1: Push your changes to the remote branch

```bash
# Make sure you're on your bug fix branch
git checkout bug/2-bug-foo-instead-of-fixme

# Add your changes
git add .

# Commit your changes
git commit -m "Fix: Change test assertion from 'fixme' to 'foo' in test_foo"

# Push to remote branch
git push origin bug/2-bug-foo-instead-of-fixme
```

### Step 2: Create Pull Request via GitHub Web Interface

1. **Go to your repository on GitHub**
2. **You'll see a yellow banner** saying "bug/2-bug-foo-instead-of-fixme had recent pushes" with a **"Compare & pull request"** button
3. **Click "Compare & pull request"**

### Step 3: Fill out the Pull Request form

**Title:**
```
Fix: Change test assertion from 'fixme' to 'foo' in test_foo
```

**Description:**
```markdown
## Bug Fix
- Fixed the failing test_foo method in test_gilded_rose.py
- Changed assertion from expecting "fixme" to expecting "foo"
- Test now passes successfully

## Changes Made
- Modified test_gilded_rose.py line 12
- Changed `self.assertEqual("fixme", items[0].name)` to `self.assertEqual("foo", items[0].name)`

## Testing
- [x] Ran `python -m unittest` - all tests pass
- [x] Verified the fix resolves the failing test

## Notes
This was an intentional test error to demonstrate the testing workflow. The test now correctly validates the expected behavior.
```

4. **Click "Create pull request"**

### Step 4: Wait for Review and Merge

1. **Wait for review** from team members (if any)
2. **Address any feedback** by pushing more commits to the same branch
3. **Once approved**, merge the PR using one of these methods:
   - **Merge commit** (recommended for feature branches)
   - **Squash and merge** (combines all commits into one)
   - **Rebase and merge** (replays commits on top of main)

## 7. Clean Up After Merge

### Step 1: Switch back to main branch

```bash
# Switch to main branch
git checkout main

# Pull the latest changes (including your merged PR)
git pull origin main
```

### Step 2: Delete the local branch

```bash
# Delete the local branch
git branch -d bug/2-bug-foo-instead-of-fixme

# If the branch hasn't been merged, use -D to force delete
# git branch -D bug/2-bug-foo-instead-of-fixme
```

### Step 3: Delete the remote branch

```bash
# Delete the remote branch
git push origin --delete bug/2-bug-foo-instead-of-fixme
```

### Step 4: Verify cleanup

```bash
# List local branches
git branch

# List remote branches
git branch -r

# Check status
git status
```

## 8. Alternative: GitHub Auto-Cleanup

If you enabled **"Delete head branch"** when creating the PR:
1. The remote branch will be **automatically deleted** after merging
2. You only need to delete the **local branch**:

```bash
# Switch to main and pull latest
git checkout main
git pull origin main

# Delete local branch
git branch -d bug/2-bug-foo-instead-of-fixme
```

## 9. Verify Everything is Clean

```bash
# Check you're on main branch
git branch

# Verify no uncommitted changes
git status

# Should show:
# On branch main
# Your branch is up to date with 'origin/main'.
# nothing to commit, working tree clean
```

Your bug fix workflow is now complete! 🎉
