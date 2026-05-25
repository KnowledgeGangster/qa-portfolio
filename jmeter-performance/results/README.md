# JMeter Test Results

## Overview
This folder contains raw execution results generated from JMeter performance test runs.

These results are used to analyze system performance under load.

## File Types
- `.jtl` files (raw JMeter result logs)
- CSV output files
- Execution logs

## Key Metrics Captured
- Response Time (Average, Min, Max)
- Throughput (requests/sec)
- Error Rate (% failures)
- Latency
- Active Threads Over Time

## Example Output File
- login-load-test-results.jtl
- checkout-stress-test-results.jtl

## How Results Are Generated
Results are generated using CLI execution:

```bash
jmeter -n -t test-plan.jmx -l results/test-results.jtl
