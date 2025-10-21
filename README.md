# Gr11CAT_Spreadsheets

Short answer: almost—but we can tighten it up for GitHub.

Here’s a **copy-paste-ready `README.md`** version with a clean title, table of contents, consistent heading levels, fenced code blocks, and GitHub-friendly tips like collapsible sections.

````markdown
# Grade 11 CAT (NCS CAPS) — Spreadsheets: Start-to-Finish Guide

> Practical Excel/Calc skills for South African Grade 11 CAT: formulas, lookups, data tools, charts, and exam printing. Works with Microsoft Excel and LibreOffice Calc.

---

## Table of Contents
- [1) Foundations](#1-foundations)
- [2) Cleaning & Formatting](#2-cleaning--formatting)
- [3) Core Formulas](#3-core-formulas)
  - [3.1 Arithmetic & Rounding](#31-arithmetic--rounding)
  - [3.2 Statistics](#32-statistics)
  - [3.3 Logic](#33-logic)
  - [3.4 Conditional Aggregates](#34-conditional-aggregates)
  - [3.5 Text Functions](#35-text-functions)
  - [3.6 Dates & Times](#36-dates--times)
- [4) Lookup & Reference](#4-lookup--reference)
- [5) Tables, Sorting, Filtering](#5-tables-sorting-filtering)
- [6) Charts & Visualisations](#6-charts--visualisations)
- [7) Printing & Page Setup](#7-printing--page-setup)
- [8) Protection & Integrity](#8-protection--integrity)
- [9) Typical Grade-11 Tasks](#9-typical-grade11-tasks)
- [10) LibreOffice Calc Notes](#10-libreoffice-calc-notes)
- [11) CAPS Alignment](#11-caps-alignment)
- [12) Speed & Exam Technique](#12-speed--exam-technique)
- [13) Common Errors & Fixes](#13-common-errors--fixes)
- [14) Practice Mini-Tasks](#14-practice-mini-tasks)
- [15) Keyboard Shortcuts](#15-keyboard-shortcuts)
- [16) Quick Reference](#16-quick-reference)
- [17) Marking Rubric Hints](#17-marking-rubric-hints)
- [18) Optional Extensions](#18-optional-extensions)

---

## 1) Foundations
**Interface & Files**
- Workbook vs Worksheet; sheet tabs; A1 notation; Name Box.
- Save as `.xlsx` / `.ods` / export `.csv`.
- View: Zoom, Page Break Preview, Freeze Panes.

**Data Types**
- Text, Number, Date, Time, Boolean. Clean with `TRIM()`.

**Selecting & Moving**
- `Ctrl+Shift+Arrow`, insert/delete rows/columns, Autofill.

**Cell Referencing**
- Relative `A2`, Absolute `$A$2`, Mixed `$A2`/`A$2` (Excel: press `F4`).

---

## 2) Cleaning & Formatting
**Number Formats**
- Currency, Percent, Date `YYYY-MM-DD`, Time `hh:mm`.
- Custom:
  - `"Qty: "0`
  - `0000` (leading zeros)
  - `[=1]"Yes";[=0]"No";"–"`

**Conditional Formatting**
- Duplicates, top/bottom N, formula rule e.g. weekends:  
  `=WEEKDAY($A2,2)>5`

**Data Validation**
- Lists, ranges, dates, custom (SA ID length): `=LEN(A2)=13`.

---

## 3) Core Formulas
### 3.1 Arithmetic & Rounding
- `=A2*B2` `=A2/B2` `=A2+B2-C2`
- `ROUND`, `ROUNDUP`, `ROUNDDOWN`, `ABS`

### 3.2 Statistics
- `SUM`, `AVERAGE`, `MIN`, `MAX`
- `COUNT`, `COUNTA`, `COUNTBLANK`

### 3.3 Logic
```excel
=IF(C2>=50,"Pass","Fail")
=IFS(C2>=80,"A",C2>=70,"B",C2>=60,"C",C2>=50,"D",TRUE,"F")
=IF(AND(C2>=50,D2="Yes"),"Promote","Hold")
````

### 3.4 Conditional Aggregates

```excel
=SUMIF(range,criteria,sum_range)
=COUNTIF(range,criteria)
=AVERAGEIF(range,criteria)
=SUMIFS($E:$E,$B:$B,"KZN",$C:$C,"Term 2")
```

### 3.5 Text Functions

```excel
=LEFT(A2,3)   =RIGHT(A2,4)
=MID(A2, FIND("-",A2)+1, 99)
=LEN(A2)  =FIND(" ",A2)  =SEARCH("x",A2)
=UPPER(A2)  =LOWER(A2)  =PROPER(A2)
=TRIM(A2)
=A2 & " " & TEXT(B2,"R 0.00")
```

### 3.6 Dates & Times

* `TODAY()`, `NOW()`, `DAY`, `MONTH`, `YEAR`, `WEEKDAY(date,2)`
* Build: `DATE(YYYY,MM,DD)`
* Differences: days `=end-start`; hours `=(end-start)*24`
  Display durations with `[h]:mm` or `[m]`
* Working days: `NETWORKDAYS(start,end,[holidays])`

---

## 4) Lookup & Reference

* **VLOOKUP** (exact): `=VLOOKUP(lookup, table, col, FALSE)`
* **XLOOKUP**: `=XLOOKUP(lookup, lookup_array, return_array, "Not found")`
* **INDEX/MATCH**: `=INDEX(ret_rng, MATCH(lookup, lookup_rng, 0))`
* Fix `#N/A` with `TRIM`, ensure exact matches; use `IFERROR`.

---

## 5) Tables, Sorting, Filtering

* Format as Table (`Ctrl+T`), structured refs, totals row.
* Multi-key sort; Text/Number filters; Advanced Filter for complex rules.

---

## 6) Charts & Visualisations

* Column/Bar (categories), Line (time), Pie (≤5 slices), Combo (target lines).
* Clear titles, labels; avoid clutter. Sparklines for in-cell trends.

---

## 7) Printing & Page Setup

* Orientation, Margins, Scaling (Fit All Columns).
* Repeat header row (Print Titles).
* Headers/Footers: Name, Class, Sheet, Page X of Y, Date.
* Manual page breaks where needed.

---

## 8) Protection & Integrity

* Protect Sheet (lock formulas; unlock inputs).
* Protect Workbook (sheet add/delete).
* Trace Precedents/Dependents; `IFERROR()` to handle edge cases.

---

## 9) Typical Grade-11 Tasks

**Invoice**

```excel
LineTotal = Qty*UnitPrice
Discount  = IF(Qty>=10, LineTotal*0.05, 0)
VAT(15%)  = LineTotal*0.15
GrandTotal = SUM(LineTotals)-SUM(Discounts)+SUM(VAT)
```

**Marks & Symbols**

```excel
Aggregate = ROUND(Test1*0.2 + Test2*0.3 + Exam*0.5, 0)
Symbol = IFS(Aggregate>=80,"A",Aggregate>=70,"B",Aggregate>=60,"C",Aggregate>=50,"D",TRUE,"E/F")
```

**Attendance/Payroll**

```excel
Hours     = (Out-In)*24        // format as [h]:mm
Overtime  = MAX(0,Hours-8)
Pay       = Hours*Rate + Overtime*Rate*1.5
```

**Regional Totals**

```excel
=SUMIFS(E:E,B:B,"KZN",C:C,"Term 2")
```

**Price Lookup**

```excel
=INDEX($J:$J, MATCH(A2,$H:$H,0))   // robust for left lookups
```

**Name Parsing**

```excel
First   = TRIM(MID(A2, FIND(",",A2)+1, 99))
Surname = TRIM(LEFT(A2, FIND(",",A2)-1))
```

---

## 10) LibreOffice Calc Notes

* `IFS` may be missing in older Calc → use nested `IF`.
* Prefer `INDEX/MATCH` (no `XLOOKUP`).
* Data Validity = Data Validation. Pivot Table = Data Pilot.

---

## 11) CAPS Alignment

* Formulas & references (relative/absolute/mixed)
* SUM/AVERAGE/MIN/MAX/COUNT*, IF(+AND/OR), text, date/time
* Sort/filter, validation, remove duplicates
* Conditional formatting, charts
* Printing (titles, scaling, headers/footers)
* Neat layout; protected formulas; documentation (comments)

---

## 12) Speed & Exam Technique

* Plan columns first; build one perfect formula then fill.
* Use absolute refs when copying across.
* Show units via formatting, not typed text.
* Sanity checks (subtotals vs totals); spot-check by hand.
* Final pass: page setup, scaling, repeated titles.

---

## 13) Common Errors & Fixes

* `#####` → column too narrow.
* Wrong totals after sort → use Tables/dynamic ranges.
* `#DIV/0!` → guard: `=IFERROR(A2/B2,0)`
* `#N/A` → spacing/mismatch; use `TRIM`, exact match.
* Times appear as decimals → apply Time or `[h]:mm` format.

---

## 14) Practice Mini-Tasks

* **Sales:** Date, Region, Product, Qty, UnitPrice, LineTotal, Discount (Qty≥12 → 7%), VAT, Net. Monthly totals via `SUMIFS`. Line chart of Net by month.
* **Results:** Year mark (`IF/IFS`), pass/fail (`AND`). Conditional format: fails red, ≥80% green.
* **Lookup:** Separate PriceList; `INDEX/MATCH` price; Data Validation dropdown for Product.
* **Timesheet:** Daily hours, overtime, weekly pay; `[h]:mm`; (Excel) `MROUND(time,"0:15")`.

---

## 15) Keyboard Shortcuts (Excel, Windows)

* `Ctrl+T` table • `Ctrl+D` fill down • `Ctrl+R` fill right
* Insert row/col: select row/col → `Ctrl+Shift+=`
* Select region: `Ctrl+A` (inside data)
* Absolute refs: `F4` • Format Cells: `Ctrl+1`
* Evaluate in formula bar: select part → `F9`

---

## 16) Quick Reference

**Logic**

```excel
=IF(test, true, false)
=IF(AND(A2>=50,B2="Yes"),"OK","No")
=IF(OR(C2="DBN",C2="JHB"),"Metro","Other")
```

**Conditional Totals**

```excel
=SUMIF(B:B,"KZN",E:E)
=COUNTIFS(B:B,"KZN",C:C,"Term 2")
=SUMIFS(E:E,B:B,"KZN",C:C,">=2025-04-01",C:C,"<=2025-06-30")
```

**Lookup**

```excel
=VLOOKUP(A2,$H:$K,3,FALSE)
=INDEX($J:$J, MATCH(A2,$H:$H,0))
=XLOOKUP(A2,$H:$H,$J:$J,"Not found")
```

**Dates & Times**

```excel
=TODAY()   =NOW()
=DATE(2025,10,21)
=(End-Start)         // days
=(End-Start)*24      // hours (format General)
```

**Rounding & Errors**

```excel
=ROUND(A2,2)  =ROUNDUP(A2,0)  =ROUNDDOWN(A2,0)
=IFERROR(A2/B2,0)
```

---

## 17) Marking Rubric Hints

* **Correctness:** formula logic + correct references
* **Efficiency:** single fill-down formulas; no hard-coding
* **Clarity:** headings, units via formatting, tidy widths
* **Validation:** restrict bad inputs
* **Presentation:** appropriate chart; proper print layout

---

## 18) Optional Extensions

* Named ranges; dynamic arrays (`UNIQUE`, `FILTER`, `SORT`)
* Goal Seek (price/profit targets)
* PivotTables for Region/Month summaries (if allowed)


