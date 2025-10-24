# 200 - Run the unit tests from the Command-Line

Your command line should start with ```(venv)```, indicating that you are working inside your virtual environment.

``` python
python -m unittest
```

The first time this will be the outcome:

The test is failing because it expects the item name to be "fixme" but it's actually "foo". This is actually expected behavior for the Gilded Rose Kata!

## What's happening:
This is a test-driven development kata where:
- The test is written first (expecting "fixme")
- The code is supposed to be implemented to make the test pass
- The current code returns "foo" instead of "fixme"

## Next Steps:
This is the intended starting point of the kata! You should now:
1. Look at the failing test to understand what it expects
2. Modify the gilded_rose.py code to make the test pass
3. Continue with the refactoring exercises