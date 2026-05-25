# Allure Reports

This folder contains test execution reports generated using Allure Framework.

## Purpose
Allure Reports provide a detailed and visual representation of automated test execution results.

They help in:
- Tracking test execution status
- Debugging failed tests
- Understanding test coverage
- Sharing test results with stakeholders

## Report Contents
Allure Reports typically include:
- Test case execution status (Pass/Fail/Skipped)
- Step-by-step execution details
- Screenshots (on failure)
- Error logs and stack traces
- Execution timeline
- Test history trends

## Integration
Allure is integrated with:
- Selenium WebDriver
- PyTest

## Example Execution Flow
```bash
pytest --alluredir=reports/
allure serve reports/
