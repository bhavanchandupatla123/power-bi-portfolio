# Example DAX Measures

These examples show the type of reusable KPI and time-intelligence measures used in my Power BI practice model.

```DAX
Total Sales =
SUM(FactSales[SalesAmount])
```

```DAX
Total Quantity =
SUM(FactSales[Quantity])
```

```DAX
Transactions =
DISTINCTCOUNT(FactSales[OrderID])
```

```DAX
Unique Customers =
DISTINCTCOUNT(FactSales[CustomerID])
```

```DAX
Sales LY =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(DimDate[Date])
)
```

```DAX
YoY Change =
[Total Sales] - [Sales LY]
```

```DAX
YoY % =
DIVIDE(
    [YoY Change],
    [Sales LY]
)
```

```DAX
Online Sales =
CALCULATE(
    [Total Sales],
    FactSales[Channel] = "Online"
)
```

```DAX
Ship Date Sales =
CALCULATE(
    [Total Sales],
    USERELATIONSHIP(FactSales[ShipDate], DimDate[Date])
)
```

## Why these measures matter

These measures support reusable KPI reporting, period comparison, channel analysis and alternate-date analysis without duplicating business logic across visuals.

> Exact table and column names should match the final model used in Power BI Desktop.
