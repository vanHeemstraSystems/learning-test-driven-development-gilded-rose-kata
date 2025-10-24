# 500 - Run the ApprovalTests.Python test

Your command line should start with ```(venv)```, indicating that you are working inside your virtual environment.

This test uses the framework [ApprovalTests.Python](https://github.com/approvals/ApprovalTests.Python). You will need to install it.

Run it like this:

```python
python tests/test_gilded_rose_approvals.py
```

You will need to approve the output file which appears under "approved_files" by renaming it from xxx.received.txt to xxx.approved.txt.
