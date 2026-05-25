# JMeter Test Plan

## Overview
This folder contains JMeter test plans used to define performance testing scenarios.

A test plan is the starting point for any performance test and defines:
- Thread groups (virtual users)
- Samplers (requests)
- Timers
- Assertions
- Listeners

## Components of a Test Plan
- Thread Group (users, ramp-up, loop count)
- HTTP Requests (API or UI endpoints)
- Config Elements (CSV Data Sets, variables)
- Assertions (validation rules)
- Listeners (results collection)

## Example Test Scenarios
- Login API load test
- Search endpoint stress test
- Checkout flow performance test
- Concurrent user simulation

## File Types
- .jmx files (JMeter test plans)
- CSV files (test data inputs)

## Execution
Test plans can be executed via CLI:

```bash
jmeter -n -t test-plan.jmx
