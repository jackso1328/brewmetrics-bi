# Copilot Notes

## Purpose

GitHub Copilot was considered as an assistant for developing and reviewing
DAX measures in the BrewMetrics Coffee Co. Power BI semantic model.

Two measures were reviewed in particular:
1. MoM Growth %
2. City Sales Rank

---

## 1. MoM Growth %

### Prompt given to Copilot

I am building a Power BI semantic model for BrewMetrics Coffee Co.
The model contains a Fact_Sales table with a sales_amount column and
a Dim_Date table with a Date column. An existing measure called
[Total Sales] is available.

Suggest a DAX measure to calculate month-over-month sales growth
percentage.

### Initial Copilot suggestion

[Paste the Copilot-generated DAX suggestion here.]

### Review and correction

The suggested formula was reviewed against the existing BrewMetrics
semantic model. The calculation needs to compare the current month's
sales with the previous month's sales using the date dimension.

The final measure used in the model was:

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
