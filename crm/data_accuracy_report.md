# Salesforce (CRM) Earnings Data — Accuracy Report

## Sources Evaluated

| Source | File | Coverage | Metrics |
|--------|------|----------|---------|
| **v1** | `salesforce_financial_data_v1.xlsx` | FY2022–FY2025 | Revenue, sub revenue, gross profit, GAAP operating income, net income, GAAP/non-GAAP EPS, OCF, FCF, CapEx (all in $B) |
| **v2** | `salesforce_financial_data_v2.csv` | FY2023–FY2026 | Revenue ($B), non-GAAP EPS, non-GAAP operating margin |
| **v3** | `salesforce_financial_data_v3.csv` | FY2023–FY2026 | Revenue, sub revenue, services revenue, gross profit, GAAP operating income, net income, GAAP EPS, RPO, OCF (all in $M) |

## Verification Methodology

All figures were cross-referenced against:
- Salesforce official quarterly earnings press releases (salesforce.com/news)
- Salesforce Investor Relations (investor.salesforce.com)
- SEC filings (10-K and 10-Q via sec.gov)
- S&P Global Market Intelligence data (via stockanalysis.com)
- GAAP operating margins from press releases were multiplied by reported revenue to independently verify operating income
- Quarterly OCF was summed and compared to official annual totals

---

## Discrepancies Found

### 1. Non-GAAP Diluted EPS — Two Errors (one in v1, one in v2)

| Quarter | v1 (xlsx) | v2 (csv) | Correct Value | Source |
|---------|-----------|----------|---------------|--------|
| FY2023 Q1 | **$1.23 (WRONG)** | $0.98 | **$0.98** | Salesforce Q1 FY23 press release (May 31, 2022) |
| FY2025 Q4 | $2.78 | **$2.27 (WRONG)** | **$2.78** | Salesforce Q4 FY25 press release (Feb 26, 2025); multiple analyst sources confirm 21% YoY growth to $2.78 |

All other non-GAAP EPS quarters agree between v1 and v2.

### 2. GAAP Operating Income — v1 Wrong for 6 Quarters

v1's "Operating Income ($B)" column contains incorrect values for FY2023 Q3 through FY2024 Q4. v3's figures (in $M) match the GAAP operating margins reported in official press releases within $4M (rounding).

| Quarter | v1 ($M equiv) | v3 ($M) | Calculated from PR GAAP Margin | v1 Error |
|---------|---------------|---------|-------------------------------|----------|
| FY2023 Q3 | 360 | **460** | 462 (5.9% × $7,837M) | -$100M |
| FY2023 Q4 | 420 | **357** | 361 (4.3% × $8,384M) | +$63M |
| FY2024 Q1 | 790 | **412** | 412 (5.0% × $8,247M) | +$378M |
| FY2024 Q2 | 1,310 | **1,476** | 1,480 (17.2% × $8,603M) | -$166M |
| FY2024 Q3 | 1,360 | **1,501** | 1,500 (17.2% × $8,720M) | -$141M |
| FY2024 Q4 | 1,550 | **1,622** | 1,625 (17.5% × $9,287M) | -$72M |

FY2025 quarters are correct in both v1 and v3.

### 3. Operating Cash Flow — v1 Wrong for FY2023

v3's quarterly OCF sums match official annual totals exactly. v1 is off by $791M for FY2023.

| Fiscal Year | v3 Sum ($M) | v1 Sum ($M) | Official Annual | v1 Error |
|-------------|-------------|-------------|-----------------|----------|
| FY2023 | **7,111** | 6,320 | ~$7.11B | -$791M |
| FY2024 | **10,234** | 10,220 | ~$10.23B | -$14M |
| FY2025 | **13,092** | 13,080 | ~$13.09B | -$12M |

The largest quarterly disagreements in FY2023:
- Q1: v1=$1,830M vs v3=$3,676M (press release confirms "$3.68 billion")
- Q4: v1=$3,720M vs v3=$2,788M (press release confirms "~$2.79 billion")

v1 appears to have swapped or misattributed Q1 and Q4 OCF values for FY2023.

### 4. Gross Profit — v1 Imprecise (Rounded to $B)

v3's gross profit figures match S&P Global Market Intelligence data exactly. v1 is rounded to hundredths of a billion, causing differences of $6–$146M.

### 5. Total RPO — v3 Wrong for FY2023 Q3

v3 lists FY2023 Q3 Total RPO as $40.8B. The official Q3 FY23 press release (November 30, 2022) states: "Remaining performance obligation ended the third quarter at $40.0 billion." No other Salesforce quarter reported $40.8B, so this is a data entry error rather than a transposition.

### 6. Revenue — Minor Rounding Differences

All three sources agree on revenue. v3 provides exact $M figures matching SEC filings. v1 and v2 round to $B. Largest rounding gaps in v2: FY2026 Q2 ($10.20B vs $10,236M) and Q3 ($10.30B vs $10,259M).

---

## Overall Accuracy Assessment

| Source | Revenue | GAAP EPS | Non-GAAP EPS | Gross Profit | GAAP Op Income | Net Income | OCF | Verdict |
|--------|---------|----------|-------------|-------------|----------------|------------|-----|---------|
| **v3** | Exact ($M) | Correct | N/A | Exact ($M) | Correct | Correct | Correct | **Most Accurate** (1 RPO error) |
| **v2** | Rounded ($B) | N/A | 1 error (FY25 Q4) | N/A | N/A | N/A | N/A | Accurate for non-GAAP (1 error) |
| **v1** | Rounded ($B) | Correct | 1 error (FY23 Q1) | Imprecise | Wrong (6 Qs) | Correct | Wrong (FY23) | Least Accurate |

### Conclusion

**v3 is the most reliable source** for GAAP financial data. It provides exact figures in millions that match SEC filings and official press releases across all metrics. v2 is accurate for non-GAAP metrics (with the FY25 Q4 EPS correction). v1 contains the most errors, particularly in GAAP operating income (FY2023–FY2024) and operating cash flow (FY2023), and should not be used as a primary source without correction.

The final CSV (`salesforce_quarterly_earnings_final.csv`) in this folder combines verified data from all three sources with corrections applied.
