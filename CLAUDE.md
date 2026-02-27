# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Salesforce (CRM) earnings data repository used for financial analysis. It currently contains raw financial data files with no application code or build system.

## Data Files

All financial data lives in `earnings_data/`:

- **v1 (xlsx)**: Original Excel source file with Salesforce financial data
- **v2 (csv)**: Summary view — fiscal year/quarter with revenue, non-GAAP EPS, and non-GAAP operating margin (FY23–FY26)
- **v3 (csv)**: Detailed GAAP view — includes subscription vs services revenue breakdown, gross profit, operating income, net income, EPS (basic/diluted), RPO, and operating cash flow (FY23 Q1–FY26 Q4)

All dollar amounts in v2 are in billions USD. In v3, all amounts are in millions USD except RPO (billions) and EPS (per share).

## Directory Structure

- `earnings_data/` — Salesforce financial data files
- `crm/` — Empty; intended for future CRM analysis code
