# PowerBi-Project

<p align="center">
	<a href="https://github.com/user-attachments/assets/18f93a36-4f48-4858-b8da-9c11575330a3">
		<img src="https://github.com/user-attachments/assets/18f93a36-4f48-4858-b8da-9c11575330a3" alt="Sample visual" width="1200" />
	</a>
</p>

## Project Overview

This project demonstrates a simple end-to-end workflow for preparing and presenting data using Microsoft Excel for data cleaning and Microsoft Power BI for analysis and visualization. The sample dataset focuses on sales performance (orders, customers, products, and dates) and shows how to transform raw data into a clean, analysis-ready model and create an interactive Power BI report.

## Why this approach

- Excel is used for initial ingestion, quick exploratory cleaning, and repeatable transformation steps when a lightweight, familiar tool is preferred.
- Power BI is used for data modelling, creating measures (DAX), and building interactive visuals for stakeholders.

## Contents / Deliverables

- Cleaned data file: `data/cleaned_sales.xlsx` (or similar) — the normalized dataset exported from Excel ready for import to Power BI.
- Power BI report: `reports/Sales_Performance.pbix` — the interactive report containing visuals, filters, and bookmarks.
- This `README.md` — project description and instructions.

## Excel: Data cleaning steps (recommended workflow)

1. Ingest raw files
	- Import CSV/CSV exports into Excel (Data > Get Data) or open raw sheets.
2. Inspect and document
	- Check for missing values, inconsistent formats (dates, numbers), duplicate rows, and outliers.
3. Normalize and standardize
	- Convert dates to a single format using Text to Columns or DATEVALUE.
	- Standardize text fields (TRIM, UPPER/LOWER) and fix inconsistent category names.
4. Remove duplicates and invalid rows
	- Use Remove Duplicates and filters to drop clearly invalid rows (blank required fields, impossible dates).
5. Split and combine fields
	- Use Text to Columns or formulas (LEFT/RIGHT/MID, FIND) to split combined fields; use CONCAT or & to combine where needed.
6. Use lookup tables
	- Create small reference tables (product codes, region codes) and use VLOOKUP/XLOOKUP or INDEX/MATCH to enrich rows.
7. Apply validation and calculated columns
	- Data Validation rules for consistent data entry; create calculated columns (e.g., SalesAmount = Quantity * UnitPrice).
8. Pivot / aggregate for checks
	- Use PivotTables to validate totals, spot-check for anomalous values, and verify transformations.
9. Document transformations
	- Keep a short notes sheet listing the steps performed and any assumptions made.
10. Export cleaned dataset
	- Save a dedicated cleaned file (XLSX or CSV) with only the columns required for analysis.

## Power BI: Presentation and modelling steps

1. Import cleaned data
	- Load the cleaned Excel/CSV file(s) into Power BI Desktop.
2. Build the data model
	- Create relationships between tables (e.g., Orders -> Customers, Orders -> Products, Dates table).
	- Add a date/calendar table for reliable time intelligence.
3. Create measures with DAX
	- Examples: Total Sales = SUM(Orders[SalesAmount])
	- YoY Growth, Running Total, and Average Order Value are common measures.
4. Design visuals
	- Choose appropriate charts (bar/column for comparisons, line charts for trends, map visuals for geography).
	- Add slicers, drillthrough, and bookmarks for storytelling.
5. Improve UX
	- Use tooltips, conditional formatting, clear axis labels, and consistent color palettes.
6. Test interactions
	- Validate filters, cross-highlighting, and drill paths work as expected.
7. Publish and share
	- Publish to Power BI Service or export PDF/PPT snapshots for distribution.

## Example assumptions and notes

- The cleaned Excel file contains one table named `Orders` with columns such as OrderID, OrderDate, CustomerID, ProductID, Quantity, UnitPrice, SalesAmount, Region.
- Sensitive or proprietary data should be removed or obfuscated before sharing.

## How to review the project

1. Open `data/cleaned_sales.xlsx` in Excel to review the cleaned dataset and the transformation notes.
2. Open `reports/Sales_Performance.pbix` in Power BI Desktop to explore visuals and measures.
3. Use the Notes sheet in Excel for a step-by-step record of cleaning logic and any formulas used.

## Next steps / Improvements

- Automate repeatable cleaning with Power Query (in Excel or Power BI) so transformations are repeatable and source-driven.
- Add unit checks or validation scripts (small macros or Power Query validation steps) to flag anomalies on import.
- Move to a shared data source (SQL / Azure / SharePoint) for collaborative updates and scheduled refreshes in Power BI Service.

## Contact / Credits

Project prepared with Excel (cleaning) and Power BI (visualization). For questions about workflows or DAX measures, contact the project owner.

---
_Last updated: Nov 9, 2025_
