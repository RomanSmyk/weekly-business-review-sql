# Weekly Business Review — SQL Automation
**Accenture for Google | Content Review Operations | EMEA | 2021**

## The Problem

As a Quality Assurance Analyst at Accenture, I was responsible for producing
a Weekly Business Review (WBR) — a recurring report tracking content review
quality metrics across EMEA markets. The metrics covered:

- **False Positives (FP):** cases where a reviewer incorrectly flagged content
- **False Negatives (FN):** cases where a reviewer missed a genuine violation

The report was broken down by Language, Site location (Krakow, Dublin, Lisbon),
Violation Topic, and individual Reviewer.

Before this script existed, the WBR was produced manually using Google Sheets —
copying, filtering, and aggregating raw data by hand each week. The process was
slow, error-prone, and had to be repeated from scratch every reporting cycle.

## The Solution

I wrote a set of SQL queries in Google BigQuery / PLX Scripting to automate the entire
extraction and aggregation process. Each query targets a specific dimension of
the report and outputs a clean, ready-to-use results table.

**Queries included:**

| # | Output |
|---|--------|
| 1 | FP and FN counts by Language |
| 2 | FP and FN counts by Site |
| 3 | FP and FN counts by Language and Violation Topic |
| 4 | FP and FN counts by Violation Topic |
| 5 | FP and FN counts by Reviewer |

## Impact

Reduced Weekly Business Review preparation time by approximately **80%**.
The manual Google Sheets process was replaced by running these queries
against the live data warehouse, with results available in seconds.

## Technical Notes

- **Platform:** Google BigQuery / PLX Scripting (Standard SQL)
- Query 1 uses CTEs to separate the review count and error count logic
  before joining, keeping each step readable and independently testable
- All queries use parameterised date placeholders (`YYYY-MM-DD`) —
  replace with the reporting period start and end dates before running
- Table name placeholders (`{TABLE_NAME}`) replace the original internal
  table references, which are not included for confidentiality reasons
- Queries 2–5 use `HAVING` to exclude language/topic/reviewer combinations
  with zero errors, keeping the output focused on actionable items

## Skills Demonstrated

SQL · Google BigQuery / PLX Scripting (Standard SQL) · CTEs · Aggregation · HAVING · Analytical Reporting
