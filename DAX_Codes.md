# Dax Codes

Here you can find the Dax codes used in this Power BI report:

### Dax Measures

    ```
    Furniture15vs14 = DIVIDE([FurnitureRevenue2015] -
        CALCULATE('DAX Measures'[Revenue],
            FILTER(Sales, Sales[Category] = "Furniture"),
            FILTER(Sales, YEAR(Sales[OrderDate]) = 2014)
        ),
        CALCULATE('DAX Measures'[Revenue],
            FILTER(Sales, Sales[Category] = "Furniture"),
            FILTER(Sales, YEAR(Sales[OrderDate]) = 2014)
        )
    )
    ```

    ```
    FurnitureRevenue15vs14 = 
    VAR FurnitureRevenue2014 = CALCULATE('DAX Measures'[Revenue],
            FILTER(Sales, Sales[Category] = "Furniture"),
            FILTER(Sales, YEAR(Sales[OrderDate]) = 2014))
    RETURN DIVIDE(([FurnitureRevenue2015] - [FurnitureRevenue2014]), 
        [FurnitureRevenue2014])
    ```

    ```
    FurnitureRevenue2014 = CALCULATE('DAX Measures'[Revenue],
            FILTER(Sales, Sales[Category] = "Furniture"),
            FILTER(Sales, YEAR(Sales[OrderDate]) = 2014) )
    ```

    ```
    FurnitureRevenue2015 = CALCULATE('DAX Measures'[Revenue],
        FILTER(Sales, Sales[Category] = "Furniture"),
        FILTER(Sales, YEAR(Sales[OrderDate]) = 2015))
    ```

    ```
    NewRevenueDiscount = SUMX(Sales, (Sales[Sales] - Sales[Sales] * Sales[SalesDiscount]))
    ```

    ```
    PreviousMonthRevenue = CALCULATE('DAX Measures'[Revenue], PREVIOUSMONTH(Dates[Date]))
    ```

    ```
    Revenue = SUM(Sales[Sales])
    ```

    ```
    Revenue MoM% = 
    DIVIDE(
        [Revenue]
            - CALCULATE([Revenue], DATEADD('Dates'[Date], -1, MONTH)),
        CALCULATE([Revenue], DATEADD('Dates'[Date], -1, MONTH))
    )
    ```

    ```
    RevenueDiscount = SUM(Sales[SalesDiscount]) 
    ```

    ```
    RevenueIncrease = 
    VAR Increase = 0.05
    RETURN 'DAX Measures'[Revenue] + ('DAX Measures'[Revenue] * Increase)
    ```

    ```
    RevenueMoM%Var = DIVIDE('DAX Measures'[RevenueMoMVar], [PreviousMonthRevenue], 0)
    ```

    ```
    RevenueMoMVar = 'DAX Measures'[Revenue] - [PreviousMonthRevenue]
    ```

    ```
    RevenueYTD = CALCULATE( 'DAX Measures'[Revenue], DATESYTD(Dates[Date]))
    ```

    ```
    SalesCount = DISTINCTCOUNT(Sales[OrderID])
    ```

### Dates Table

    ```
    Dates = CALENDARAUTO(12)
    ```

    ```
    DayName = FORMAT(Dates[Date], "ddd")
    ```

    ```
    MonthName = FORMAT(Dates[Date], "mmm")
    ```

    ```
    MonthsNumber = MONTH(Dates[Date])
    ```

    ```
    Quarter = FORMAT(Dates[Date], "\QQ")
    ```

    ```
    Year = YEAR(Dates[Date])
    ```

### Sales Table

    ```
    SalesDiscount = Sales[Sales] - (Sales[Discount] * Sales[Sales])
    ```

    ```
    Order2Ship = DATEDIFF(Sales[OrderDate], Sales[ShipDate], DAY)
    ```


