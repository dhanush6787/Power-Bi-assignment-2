# E-Commerce Sales Analysis: Power BI (DAX and Data Visualization)

Power BI Assignment 2 of the Data Analytics module. This project continues the E-Commerce Sales data model from Assignment 1 and adds DAX calculated columns, DAX measures and an interactive dashboard.

## Project Files

| File | Description |
|------|-------------|
| `PowerBI_Assignment2.pbix` | Power BI report with the data model, calculated columns, measures and visuals |
| `PowerBI_Assignment2_Report.pdf` | Screenshots of the DAX formulas, visuals and dashboard layout, with a short explanation for each |
| `README.md` | Project overview |

## Dataset

| Table | Columns |
|-------|---------|
| List of Orders | Order ID, Order Date, Customer Name, City, State, Category, Amount, Profit |
| Order Details | Order ID, Category, Sub-Category, Quantity, Amount, Profit |
| Sales Target | Category, Month of Order Date, Target |

The tables are related through Order ID (List of Orders to Order Details) and Category (Sales Target).

## DAX Calculated Columns (Order Details table)

```
Category Type = 'Order Details'[Category] & " - " & 'Order Details'[Sub-Category]
```

```
Revenue per Order = 'Order Details'[Amount] * 'Order Details'[Quantity]
```

```
Sales Category =
IF (
    'Order Details'[Amount]
        >= CALCULATE ( AVERAGE ( 'Order Details'[Amount] ), ALL ( 'Order Details' ) ),
    "Above Average",
    "Below Average"
)
```

| Column | Purpose |
|--------|---------|
| Category Type | Combines Category and Sub-Category into one label |
| Revenue per Order | Amount multiplied by Quantity for each row |
| Sales Category | Marks each row as Above Average or Below Average based on Amount |

## DAX Measures

```
Order Count = DISTINCTCOUNT ( 'Order Details'[Order ID] )
```

```
Average Profit in Delhi =
CALCULATE (
    AVERAGE ( 'Order Details'[Profit] ),
    'List of Orders'[City] = "Delhi"
)
```

```
YTD Sales = TOTALYTD ( [Total Sales], 'List of Orders'[Order Date] )
```

```
Total Sales = SUM ( 'Order Details'[Amount] )
```

```
Total Target = SUM ( 'Sales target'[Target] )
```

```
Min Target = MIN ( 'Sales target'[Target] )
```

```
Total Profit = SUM ( 'Order Details'[Profit] )
```

```
Total Quantity = SUM ( 'Order Details'[Quantity] )
```

```
Max Profit Margin = MAX ( 'Order Details'[Profit Margin] )
```

In the report file, the Order Count measure is named **Total Orders**, because a table called Order Count already exists in the model.

## Visualizations

| Visual | Chart type | Fields |
|--------|-----------|--------|
| Sales Target Achievement by Category | Clustered column chart | Category, Total Sales, Total Target |
| Max Profit Margin by Sub-Category | Donut chart | Sub-Category, Max Profit Margin |
| Monthly Sales Trend | Line chart | Order Date (Year, Month), Total Sales |
| Profit vs Quantity by Sub-Category | Scatter chart | Sub-Category, Total Quantity, Total Profit |
| Total Sales and Total Target | Cards | Total Sales, Total Target |
| Minimum Target by Category | Multi-row card | Category, Min Target |
| Sales Performance Matrix | Matrix | Category, Month, Total Sales, Total Target |
| Geographic Sales Analysis | Map | City, Total Sales |
| Sales Distribution by Sub-Category | Treemap | Sub-Category, Total Sales |
| Order Count by State | Funnel chart | State, Total Orders |

## Key Insights

1. Total sales are about ₹431.5K against a total target of about ₹435.9K, which is roughly 99% of the target.
2. The clustered column chart compares actual sales with the target for each category, so categories that fall short are easy to spot.
3. The funnel chart ranks the states by number of orders, with the highest order counts at the top.

## How to Open

1. Install Power BI Desktop (free from Microsoft).
2. Download `PowerBI_Assignment2.pbix` from this repository.
3. Open the file in Power BI Desktop.
4. Open the PDF report to see the formulas and visuals with explanations.

## Skills Demonstrated

1. DAX calculated columns and measures
2. Time intelligence (year-to-date sales)
3. Data modeling and relationships
4. Data visualization and dashboard design
5. Sales performance analysis

## Author
Dhanush.E.K

Dhanush
GitHub: [github.com/dhanush6787](https://github.com/dhanush6787)
