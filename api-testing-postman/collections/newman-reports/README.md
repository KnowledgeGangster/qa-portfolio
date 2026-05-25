# Newman Reports

This folder contains automated API test execution reports generated using Newman (Postman CLI).

## Purpose
Newman is used to run Postman collections from the command line and generate test reports.

This demonstrates:
- API automation
- CI/CD readiness
- command-line execution of tests

## Report Types
- HTML reports (visual execution summary)
- JSON reports (raw execution data)
- CLI output logs

## What These Reports Show
Each report typically includes:
- Total requests executed
- Passed/failed tests
- Assertion results
- Response times
- Error logs (if any)

## Example Execution Command
```bash
newman run collection.json -e environment.json -r html
