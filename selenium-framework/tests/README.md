# Tests

This folder contains automated UI test scripts written using Selenium WebDriver and PyTest.

## Purpose
The `tests/` directory is responsible for validating application functionality through automated UI testing.

## What This Folder Includes
- Functional test cases
- UI validation tests
- Regression tests
- Negative test scenarios
- Smoke tests

## Example Test Cases
- test_login_valid_credentials.py
- test_login_invalid_credentials.py
- test_checkout_flow.py
- test_form_validation.py

## Test Execution
Tests are executed using PyTest:

```bash
pytest tests/
