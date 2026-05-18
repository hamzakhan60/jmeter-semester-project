# JMeter Performance Testing — CSE482 Software Testing

## Student Information
- **Name:** Hamza Khan
- **Registration No:** FA22-BSE-064
- **Course:** CSE482 - Software Testing
- **Instructor:** Ms. Yella Mehroze
- **Semester:** 8th — Spring 2026

---

## Project Overview
This repository contains Apache JMeter performance test plans and an automated CI/CD pipeline using GitHub Actions for the CSE482 Software Testing course terminal lab assignment.

---

## Repository Structure
jmeter-semester-project/
├── tests/
│   └── load_test.jmx        # JMeter load test plan (50 users)
├── .github/
│   └── workflows/
│       └── jmeter.yml       # GitHub Actions CI/CD pipeline
└── README.md

---

## Test Configuration

### Load Test (Task 2A)
| Setting | Value |
|---|---|
| Virtual Users | 50 |
| Ramp-Up Period | 30 seconds |
| Loop Count | 10 |
| Duration | 120 seconds |
| Target Endpoint | GET https://jsonplaceholder.typicode.com/posts |

---

## Service Level Agreement (SLA) Targets

| Metric | Target | Result | Status |
|---|---|---|---|
| Avg Response Time | < 2000ms | 556ms | ✅ PASS |
| 90th Percentile | < 3000ms | 865ms | ✅ PASS |
| Error Rate | < 1% | 0.00% | ✅ PASS |
| Throughput | ≥ 5 req/s | 14.94/s | ✅ PASS |

---

## Stress Test Results

| Run | Users | Avg Response | Error % | Breaking Point |
|---|---|---|---|---|
| Run 1 | 25 | 468ms | 0.00% | No |
| Run 2 | 75 | 798ms | 0.00% | No |
| Run 3 | 150 | 599ms | 0.00% | No |
| Run 4 | 300 | 7011ms | 0.07% | ⚠️ Degradation |

---

## CI/CD Pipeline

This repository uses **GitHub Actions** to automatically run performance tests on every push to the `main` branch.

### Pipeline Steps:
1. Checkout repository
2. Set up Java 11 (Temurin)
3. Download Apache JMeter 5.6.3
4. Run load test in headless mode
5. Generate HTML dashboard report
6. Upload report as downloadable artifact

### How to View Results:
1. Go to **Actions** tab in this repository
2. Click the latest workflow run
3. Download **jmeter-report** artifact
4. Open `index.html` in your browser

---

## Tasks Completed

### Task 1 — Foundations
- [x] JMeter GUI orientation (5 components identified)
- [x] GET /posts/1 request — HTTP 200 ✅
- [x] POST /posts — HTTP 201 ✅
- [x] PUT /posts/1 — HTTP 200 ✅
- [x] DELETE /posts/1 — HTTP 200 ✅
- [x] Response Code Assertion
- [x] Response Body Assertion
- [x] JSON Path Assertion
- [x] Intentional failure demonstration

### Task 2 — Performance Testing
- [x] 50-user load test with SLA evaluation
- [x] Stress test (25/75/150/300 users)
- [x] CSV data-driven testing (5 post IDs)
- [x] Correlation (JSON Extractor + chained requests)

### Task 3 — CI/CD Integration
- [x] Non-GUI headless mode execution
- [x] HTML dashboard report generated
- [x] GitHub Actions pipeline configured
- [x] Automated test on every push

---

## How to Run Locally

### Prerequisites
- Java JDK 11+
- Apache JMeter 5.6.3

### Command
```bash
jmeter -n -t tests/load_test.jmx -l results/results.jtl -e -o reports/
```

### View Report
Open `reports/index.html` in any browser.

---

## Tools Used
- **Apache JMeter 5.6.3** — Performance testing
- **JSONPlaceholder API** — Test endpoint
- **GitHub Actions** — CI/CD automation
- **Java 21 (Temurin)** — Runtime environment