# DAX Formulas for Regional Sales Dashboard
## 1. Total Sales
```dax
Total Sales = SUM(Sales[Revenue])
```
## 2. Year-over-Year Growth
```dax
YoY Growth = ( [This Year's Sales] - [Last Year's Sales] ) / [Last Year's Sales]
```
## 3. Profit Margin
```dax
Profit Margin = DIVIDE(SUM(Sales[Profit]), SUM(Sales[Revenue]), 0)
```
## 4. Previous Year
``` dax
Previous Year = 
VAR _selected_year = SELECTEDVALUE('Calendar'[Year])
VAR _perv_year = _selected_year - 1
RETURN
"vs " & _perv_year & ":"
```
## 5. Orders
```dax
Orders = COUNT(Regional_data[Order ID])
```
### A. Orders Color
```dax
Orders Color = 
IF(  
    [Orders Variance] >= 0,  
    "Green",  
    "Red"  
)
```
### B. Orders Growth
```dax
Orders Growth = 
DIVIDE([Orders Variance],
[Orders PY]
)
```
### C. Orders Growth Arrow
```dax
Orders Growth Arrow = 
IF(  
    ISBLANK([Orders]),  
    BLANK(),  
    IF(  
        [Orders Variance] > 0,  
        "*" & ROUND([Orders Growth] * 100, 1) & "%" & "▲",  
        ROUND([Orders Growth] * 100, 1) & "%" & "▼"  
    )  
)
```
### D. Orders Previous Year
``` dax
Orders PY = 
CALCULATE([Orders],
PREVIOUSYEAR('Calendar'[Date])
)
```
### E. Orders Same Period Last Year
``` dax
Orders Same Period LY = 
CALCULATE([Orders],
SAMEPERIODLASTYEAR('Calendar'[Date])
)
```
### F. Orders Variance
``` dax
Orders Variance = 
[Orders] - [Orders PY] 
```
### G. Orders Minimum and Maximum Values
``` dax
Orders_Min_Max = 
VAR max_value =
    MAXX(
        ALLSELECTED(
            'Calendar'[Monthnum],
            'Calendar'[Month]
        ),
        [Orders]
    )

VAR min_value =
    MINX(
        ALLSELECTED(
            'Calendar'[Monthnum],
            'Calendar'[Month]
        ),
        [Orders]
    )

RETURN
    IF(
        [Orders] = min_value,
        "#F9OE1",
        IF(
            [Orders Variance] = max_value,
            "#C20E2E",
            "#FFAFAFD"
        )
    )
```
## 6. Calendar
``` dax
Calendar = 
    ADDCOLUMNS(
        CALENDARAUTO(),
        "Year", YEAR([Date]),
        "Month", FORMAT([Date], "mm"),
        "Monthnum", MONTH([Date]),
        "Day", DAY([Date]),
        "Weekday", FORMAT([Date], "ddd"),
        "Weeknum", WEEKDAY([Date]),
        "Qtr", "Q" & FORMAT([Date], "Q"),
        "WeekType", IF(WEEKDAY([Date]) = 7 || WEEKDAY([Date]) = 1, "Weekend", "Weekday")
    )

```


