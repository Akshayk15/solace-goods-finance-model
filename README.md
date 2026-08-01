Solace Goods — Dynamic 3-Scenario Financial Model

A 12-month financial model for a fictional D2C home fragrance brand, built to demonstrate formula-driven scenario modeling — dynamic, assumption-driven financial forecasting rather than static historical reporting.

What This Project Demonstrates

This model projects forward and lets a single dropdown instantly recalculate an entire 12-month financial picture — revenue growth, costs, cash runway, and breakeven — across three business scenarios: Best Case, Base Case, and Worst Case.

Key Features
One-click scenario switching — a single dropdown on the Dashboard drives every number and chart in the model via INDEX/MATCH lookups into a Scenarios sheet
Risk flagging — a "Months to Cash-Out" metric automatically flags if/when the business would run out of cash under the selected scenario
Breakeven analysis — contribution-margin-based breakeven revenue, compared directly against actual Month 1 revenue in a bar chart
Cash flow trajectory chart — a 12-month cumulative cash balance line with a ₹0 reference line marking the "danger zone"
4 dynamic KPI cards — Ending Cash Balance, Total Net Cash Flow, Months to Cash-Out, and Breakeven Revenue, all formula-linked and updating live
Screenshots

Best Case Show Image

Base Case Show Image

Worst Case Show Image

Technical Approach
Scenario engine: INDEX(Scenarios!range, MATCH(Dashboard!D7, Scenarios!A4:A6, 0)) pulls active Growth Rate, COGS%, and Marketing% based on the Dashboard dropdown selection
Revenue compounding: Month-over-month revenue growth uses an absolute-referenced growth rate so it compounds correctly when copied down across all 12 months
Cash-out detection: IFERROR(MATCH(TRUE, INDEX(G9:G20<0,0), 0), "12+ months") finds the first month cash balance would go negative, or returns a clean fallback message
Breakeven formula: Fixed Costs ÷ (1 − COGS% − Marketing%) — standard contribution-margin breakeven math
KPI cards: built with formula-linked text boxes (not raw cell text), since shapes always float above cells in Excel
Lesson Learned

Excel's shape/text-box formula linking only supports a direct single-cell reference — it cannot evaluate an expression like =SUM(range) directly. Any KPI card needing an aggregated value (e.g. Total Net Cash Flow) required a small helper cell on the Calculations sheet holding the SUM, with the text box then linking to that single cell.

Tools Used

Excel — Data Validation (dropdown control), INDEX/MATCH, IFERROR, formula-linked shapes, custom KPI card design, dynamic chart data ranges
