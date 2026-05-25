# JMeter Performance Testing Project

## Overview
This project demonstrates performance, load, and stress testing using Apache JMeter.

It focuses on measuring application behavior under different levels of user load.

## Tools Used
- Apache JMeter
- CSV Data Sets
- HTML Report Generator
- Listener Reports

## Types of Testing Covered
- Load Testing
- Stress Testing
- Spike Testing
- Endurance Testing

## Key Metrics Captured
- Response Time (Average, Min, Max)
- Throughput
- Error Rate
- Active Threads
- Latency

## Project Structure
- test-plan/
- results/
- reports/
- data-files/

## Example Test Scenarios
- Login load test
- API endpoint stress test
- Search functionality performance test
- Checkout flow under load

## Execution
Test execution is performed via CLI or JMeter GUI:

```bash
jmeter -n -t test-plan.jmx -l results.jtl -e -o reports/
