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


## Fixing the Issue: 'foo found but fixme expected'

In fact the error is not in de application (here: ```gilded_rose.py```), but in the unit test itself (here: ```test_gilded_rose.py```) in the test ```test_foo```:

```
    def test_foo(self):
        items = [Item("foo", 0, 0)]
        gilded_rose = GildedRose(items)
        gilded_rose.update_quality()
        self.assertEqual("fixme", items[0].name)
```

It can be easily fixed as follows:

```
    def test_foo(self):
        items = [Item("foo", 0, 0)]
        gilded_rose = GildedRose(items)
        gilded_rose.update_quality()
        self.assertEqual("foo", items[0].name) # changed "fixme" to "foo"
```

When running the unit tests again, the error has gone:

``` python
python -m unittest
```

The outcome is:

```
.
----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
```

The test was **intentional** faulty, so we would have an idea of the unit tests running well - it’s just showing you how the test structure works.

Next step is to create additional unit tests that cover the application's logic to fullfill all requirements set at the start. This we will pick up in their own section.

Now we can commit the change back to the branch and start a pull request for merging with the main branch.