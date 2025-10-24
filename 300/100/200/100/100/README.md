# 100 - Work on your fix: "fixme instead of foo"

## Finding the Issue: 'foo found but fixme expected'

### Step 1: Run the failing test to see the error

```bash
# Make sure you're in the python directory with your virtual environment activated
cd /path/to/learning-test-driven-development-gilded-rose-kata/python
source ../venv/bin/activate  # or wherever your venv is located

# Run the unit tests to see the failure
python -m unittest
```

### Step 2: Analyze the test failure output

You should see output similar to:
```
F
======================================================================
FAIL: test_foo (tests.test_gilded_rose.GildedRoseTest.test_foo)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/path/to/tests/test_gilded_rose.py", line 12, in test_foo
    self.assertEqual("fixme", items[0].name)
AssertionError: 'fixme' != 'foo'
- fixme
+ foo

----------------------------------------------------------------------
Ran 1 test in 0.001s

FAILED (failures=1)
```

### Step 3: Examine the failing test

```bash
# Look at the test file to understand what it expects
cat tests/test_gilded_rose.py
```

Look for the `test_foo` method. It should contain something like:
```python
def test_foo(self):
    items = [Item("foo", 0, 0)]
    gilded_rose = GildedRose(items)
    gilded_rose.update_quality()
    self.assertEqual("fixme", items[0].name)  # This line is failing
```

### Step 4: Examine the current implementation

```bash
# Look at the gilded_rose.py file to see what's actually happening
cat gilded_rose.py
```

### Step 5: Identify the problem

The issue is that:
- **Test expects**: The item name should be "fixme" after processing
- **Current behavior**: The item name remains "foo" 
- **Root cause**: The `update_quality()` method in `GildedRose` class is not changing the item name from "foo" to "fixme"

### Step 6: Locate the specific code that needs fixing

Look for the `update_quality` method in `gilded_rose.py`. The problem is likely in this method where it should be changing the item name but isn't.

### Step 7: Understand the business logic

Based on the test, the expected behavior is:
1. Create an item with name "foo"
2. Process it through `GildedRose.update_quality()`
3. The item name should change to "fixme"

### Step 8: Verify your understanding

```bash
# Run the test again to confirm the issue
python -m unittest tests.test_gilded_rose.GildedRoseTest.test_foo -v
```

This will show you exactly which test is failing and what the expected vs actual values are.


TO DO: FIX IT