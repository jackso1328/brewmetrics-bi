# BrewMetrics Coffee Co. - Business Intelligence Project

## Project Purpose

BrewMetrics Coffee Co. is a coffee business with Flagship, Kiosk, and Drive-Thru stores operating across four cities. This project develops a version-controlled Power BI business intelligence solution to help explore sales performance, seasonal product patterns, and city-level differences.

The project is maintained as a Power BI Project (`.pbip`) and stored in GitHub so that changes to the data model, DAX measures, dashboard, and documentation can be tracked and reviewed through version history.

## Data Model

The source data contains approximately 15,500 sales transactions covering April through June.

The Power BI model uses a star-schema structure:

- **Fact_Sales** — central transaction table containing sales information such as date, city, store format, item, quantity, unit price, and sales amount.
- **Dim_Date** — date dimension used for time-based analysis.
- **Dim_City** — city dimension used for geographic and city-level analysis.
- **Dim_Product** — product/item dimension used for product-level analysis.
- **Dim_StoreFormat** — store-format dimension used to analyse Flagship, Kiosk, and Drive-Thru performance.

The dimension tables connect to the Fact_Sales table through one-to-many relationships, allowing the report to filter and analyse sales from different perspectives.

## DAX Measures

The semantic model includes measures for:

- Total Sales
- Total Quantity
- Month-over-Month (MoM) Growth %
- Running Total Sales
- City Sales Rank using `RANKX`
- Average Sales per Transaction

These measures support trend analysis, cumulative performance, city ranking, and other business analysis in the dashboard.

## Dashboard

The dashboard provides interactive analysis of sales performance. It includes:

- Sales summary information
- Time-based analysis of product sales
- City-level sales comparison
- Product-level analysis
- A city slicer for interactive filtering
- A City → Store Format drill-down hierarchy

The drill-down allows users to move from overall city performance to the performance of different store formats within a city.

## Key Insights

### 1. Cold Brew shows a seasonal sales pattern

The dataset shows a noticeable spike in Cold Brew sales during April and May. This makes Cold Brew an important product for examining seasonal demand patterns and changes in sales over time.

### 2. Bengaluru consistently outperforms the other cities

Bengaluru shows consistently higher sales performance compared with the other three cities in the dataset. The city ranking and city-level dashboard analysis make this difference visible.

### 3. Store format provides another level of performance analysis

The City → Store Format drill-down allows city-level performance to be examined in more detail by comparing Flagship, Kiosk, and Drive-Thru stores within each city.

## Version Control

The project uses GitHub to maintain an auditable development history. The repository contains the Power BI Project, report and semantic model files, documentation, and supporting project files.

The intended development sequence is:

1. README and project setup
2. Star schema and relationships
3. DAX measures
4. Dashboard development
5. Documentation and reflection
6. Final dashboard export

The Git history is retained so that project development can be reviewed rather than treating the Power BI report as a single final file.

## Tools Used

- Microsoft Power BI Desktop
- Power BI Project (`.pbip`)
- GitHub
- Visual Studio Code
- GitHub Copilot
- DAX
- Power Query
