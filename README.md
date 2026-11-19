# HDFC Bank Service Request Resolution Analytics

A Python and Pandas notebook (Google Colab) that turns scattered banking service-request data into a clean, prioritised work queue for a customer service operations team.

> All data is fictional training data, not real HDFC Bank records.

## Problem
Service requests, status updates, customers, branches, support tickets and complaints sit in separate files and contain errors (duplicate IDs, impossible dates, mixed spellings, records pointing to requests that do not exist). The operations team cannot easily see which requests missed their SLA (deadline), which customers are unhappy, or which cases to handle first.

## What the notebook does (10 milestones)
| # | Milestone | Output |
|---|---|---|
| 1 | Load and inspect service requests | `requests_df` |
| 2 | Load customers, branches, tickets, updates, complaints | five raw DataFrames |
| 3 | Clean requests (duplicates, labels, dates, numbers) | `requests_clean` |
| 4 | Clean customer and event records, check broken links | `*_clean` tables |
| 5 | Measure SLA breaches using a data-derived snapshot date | `sla_df`, `category_sla_summary` |
| 6 | Join branch and customer details, branch metrics | `requests_enriched`, `branch_sla_summary` |
| 7 | Aggregate complaints, tickets and updates per request | `*_by_request` |
| 8 | One row per request with all evidence | `final_requests_df` |
| 9 | Priority triage from four signals | High / Medium / Low + recommended action |
| 10 | Reports and findings | three exported files |

## Priority rule
Four yes/no signals are added up: SLA breached, severe open complaint, escalated ticket, repeat request by the same customer in the same category. Score 2 or more is **High**, 1 is **Medium**, 0 is **Low**.

## How to run
1. Open `HDFC_Service_Request_Analytics_Completed.ipynb` in Google Colab.
2. Run all cells. When asked, upload `service_requests.csv`, `request_status_updates.xlsx` and `service_evidence.json`.
3. The last cell shows the automated self-check (expected 100/100).

## Outputs (created in `hdfc_reports/`)
* `hdfc_request_resolution_report.csv`: every request, High first
* `hdfc_priority_summary.csv`: counts per priority
* `hdfc_branch_sla_summary.xlsx`: branch breach metrics

## Key results
* 4,030 of 4,992 requests (80.7%) breached their SLA; 2,628 are still open past the deadline.
* Digital Banking has the highest breach rate (89.2%).
* Priority split: High 50.6%, Medium 41.5%, Low 7.9%.
* Data issues handled: 8 duplicate request IDs, 90 orphan event records, 11 requests with unusable dates.

## Tools
Python, Pandas, NumPy, Google Colab. Input formats: CSV, JSON, Excel. Output formats: CSV, Excel.

## AI usage
Edit this section to describe honestly how AI assistance was used and who approved it.
