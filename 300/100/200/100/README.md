# 100 - Fixing bug "foobar instead of fixme"

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

Accept the proposed name of the new branch (here: ```1-bug-foo-instead-of-fixme```) , choose **Main** as branch source (optionally choose ```Checkout locally```, although we will work from our remote repository) and choose **Create Branch**.




WE ARE HERE 



So lets create a new branch for the bug.

```
# 1. Create and switch to a new branch
git checkout -b bug/foo-instead-of-fixme

# 2. Or alternatively, create the branch first then switch
git branch bug/foo-instead-of-fixme
git checkout bug/foo-instead-of-fixme
```

You should see something like:

```
branch 'bug/2-bug-foo-instead-of-fixme' set up to track 'origin/bug/2-bug-foo-instead-of-fixme'.
Switched to a new branch 'bug/2-bug-foo-instead-of-fixme'
```

# 3. Work on your fix while in the virtual environment

See [README.md](./100/README.md)

# 4. When done, commit and push:

```
git add .
git commit -m "Fix: Change item name from 'foo' to 'fixme'"
git push origin bug/2-bug-foo-instead-of-fixme
```

After pushing your branch, you can create a Pull Request (PR) in several ways. Here are the most common methods:

## Method 1: GitHub Web Interface (Recommended)
1. Go to your repository on GitHub
2. You'll see a yellow banner saying "bug/2-bug-foo-instead-of-fixme had recent pushes" with a "Compare & pull request" button
3. Click "Compare & pull request"
4. Fill out the PR form:
- Title: "Fix: Change item name from 'foo' to 'fixme'"
- Description: Explain what the bug was and how you fixed it
- Reviewers: Add any team members who should review
5.Click "Create pull request"

## Method 2: GitHub CLI (if you have it installed)

### Installing GitHub CLI

#### macOS (using Homebrew)
```bash
# Install Homebrew if you don't have it
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install GitHub CLI
brew install gh
```

#### macOS (using MacPorts)
```bash
sudo port install gh
```

#### Windows (using Chocolatey)
```powershell
# Install Chocolatey if you don't have it
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

# Install GitHub CLI
choco install gh
```

#### Windows (using Scoop)
```powershell
# Install Scoop if you don't have it
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
irm get.scoop.sh | iex

# Install GitHub CLI
scoop install gh
```

#### Linux (Ubuntu/Debian)
```bash
# Add GitHub CLI repository
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null

# Update package list and install
sudo apt update
sudo apt install gh
```

#### Linux (Fedora/RHEL/CentOS)
```bash
# Add GitHub CLI repository
sudo dnf install 'https://github.com/cli/cli/releases/download/v2.40.1/gh_2.40.1_linux_amd64.rpm'
```

#### Manual Installation (All Platforms)
```bash
# Download the latest release from GitHub
# Visit: https://github.com/cli/cli/releases/latest
# Download the appropriate package for your OS and architecture
```

### Authenticating with GitHub CLI

```bash
# Authenticate with GitHub (opens browser for login)
gh auth login

# Choose your preferred protocol (HTTPS recommended)
# Choose your preferred authentication method (Login with a web browser)
# Follow the browser prompts to complete authentication
```

### Creating a Pull Request with GitHub CLI

```bash
# 1. Navigate to your repository root
cd /path/to/your/repository

# 2. Create a Pull Request from your current branch
gh pr create --title "Fix: Change item name from 'foo' to 'fixme'" --body "## Bug Fix
- Fixed the test failure where item name was 'foo' instead of expected 'fixme'
- Updated gilded_rose.py to return correct item name
- All tests now pass

## Changes Made
- Modified the item creation logic in gilded_rose.py
- Ensured test_gilded_rose.py test_foo() passes

## Testing
- [x] Ran \`python -m unittest\` - all tests pass
- [x] Verified the fix resolves the failing test"

# 3. Or create a PR interactively (will prompt for title and body)
gh pr create

# 4. View your PR in the browser
gh pr view --web

# 5. Check PR status
gh pr status
```

### Additional GitHub CLI Commands

```bash
# List all PRs
gh pr list

# View a specific PR
gh pr view [PR_NUMBER]

# Edit a PR
gh pr edit [PR_NUMBER]

# Merge a PR
gh pr merge [PR_NUMBER]

# Close a PR
gh pr close [PR_NUMBER]

# Check out a PR locally
gh pr checkout [PR_NUMBER]
```

## Method 3: Direct URL
You can also create a PR by going directly to:

```
https://github.com/YOUR_USERNAME/YOUR_REPO/compare/bug/2-bug-foo-instead-of-fixme
```

## What to Include in Your PR:

### Title:
```
Fix: Change item name from 'foo' to 'fixme'
```

### Description:
```
## Bug Fix
- Fixed the test failure where item name was 'foo' instead of expected 'fixme'
- Updated gilded_rose.py to return correct item name
- All tests now pass

## Changes Made
- Modified the item creation logic in gilded_rose.py
- Ensured test_gilded_rose.py test_foo() passes

## Testing
- [x] Ran `python -m unittest` - all tests pass
- [x] Verified the fix resolves the failing test
```

## After Creating the PR:

1. Wait for review from team members
2. Address any feedback by pushing more commits to the same branch
3. Once approved, merge the PR
4. Delete the branch after merging (GitHub usually offers this option)

The web interface method is the most user-friendly and gives you a nice visual interface to set up your PR properly!