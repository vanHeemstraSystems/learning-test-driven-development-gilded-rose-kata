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
git push origin bug/foo-instead-of-fixme
```

MORE