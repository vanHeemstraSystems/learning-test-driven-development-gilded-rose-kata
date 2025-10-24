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
```

So lets create a new branch for the bug.

```
# 1. Create and switch to a new branch
git checkout -b bug/foobar-instead-of-fixme

# 2. Or alternatively, create the branch first then switch
git branch bug/foobar-instead-of-fixme
git checkout bug/foobar-instead-of-fixme
```

MORE