# Copilot Notes

## 1. MoM Growth %

### Prompt

I am building a Power BI semantic model for BrewMetrics Coffee Co. The model contains a Fact_Sales table with a sales_amount column and a Dim_Date table with a Date column. An existing measure called [Total Sales] is available.

Suggest a DAX measure to calculate month-over-month sales growth percentage.

### Initial Copilot Suggestion

The initial suggestion was reviewed against the existing Power BI model to ensure that it used the correct table, column, and existing measure names.

### Correction and Final Version

The formula was corrected/reviewed to compare the current month's sales with the previous month's sales using the Dim_Date table.

```DAX
MoM Growth % =
VAR CurrentSales = [Total Sales]
VAR PreviousMonthSales =
    CALCULATE(
        [Total Sales],
        DATEADD(Dim_Date[Date], -1, MONTH)
    )
RETURN
    DIVIDE(
        CurrentSales - PreviousMonthSales,
        PreviousMonthSales
    )
```

The measure was formatted as a percentage.

## 2. City Sales Rank

### Prompt

I am building a Power BI semantic model for BrewMetrics Coffee Co. The model contains a Dim_City table with a City column and an existing [Total Sales] measure.

Suggest a DAX measure using RANKX to rank cities by Total Sales, with the highest-selling city receiving rank 1.

### Initial Copilot Suggestion

The initial suggestion was reviewed to ensure that the ranking compared each city against all cities in the dataset.

### Correction and Final Version

The formula was reviewed and adjusted to use ALL(Dim_City[City]) so that the ranking is calculated across the complete set of cities.

```DAX
City Sales Rank =
RANKX(
    ALL(Dim_City[City]),
    [Total Sales],
    ,
    DESC,
    DENSE
)
```

Using DESC makes the city with the highest sales rank 1. DENSE ranking gives consecutive rank values when two cities have the same sales.

## Summary

Copilot was used as a starting point for DAX development and review. The suggested formulas were checked against the actual BrewMetrics semantic model rather than being accepted without review. The final measures were adjusted to match the existing table names, relationships, and measures in the Power BI project.
