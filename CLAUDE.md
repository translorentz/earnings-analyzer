# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Multi-stock quarterly earnings data repository. Raw source data is collected, cross-verified for accuracy, and consolidated into a final corrected CSV per ticker.

## Repository Structure

Each stock gets its own ticker-named directory (e.g., `crm/`) containing:
- Raw source data files in an `earnings_data/` subdirectory
- `data_accuracy_report.md` — cross-source verification findings
- `<company>_quarterly_earnings_final.csv` — corrected, consolidated dataset

## Workflow

1. Collect multiple independent sources of quarterly earnings data for a stock
2. Compare all sources systematically for discrepancies
3. Verify disputed figures against official earnings press releases and SEC filings
4. Write an accuracy report documenting which source is correct for each metric
5. Produce a final corrected CSV combining the best data from all sources
