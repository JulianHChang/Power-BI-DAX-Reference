# Time Patterns


Basic Pattern Example

Sales := SUM ( Sales[SalesAmount] )


[SalesYTD] := 
CALCULATE (
    [Sales], 
    FILTER (
        ALL ( 'Date' ), 
        'Date'[Year] = MAX ( 'Date'[Year] )
            && 'Date'[Date] <= MAX ( 'Date'[Date] )
    )
)



Complete Pattern


[AggregationOverTime] := 
CALCULATE (
    [OriginalMeasure], 
    FILTER (
        ALL ( 'Date' ), 
        <check whether the date belongs to the aggregation>
    )
)



[YTD] := 
CALCULATE (
    [OriginalMeasure], 
    FILTER (
        ALL ( 'Date' ), 
        'Date'[Year] = MAX ( 'Date'[Year] )
            && 'Date'[Date] <= MAX ( 'Date'[Date] )
    )
)



= COUNTROWS (
    FILTER (
        ALL ( Date ), 
        'Date'[Date] <= EARLIER ( 'Date'[Date] )
            && NOT ( MONTH ( 'Date'[Date] ) = 2 && DAY ( 'Date'[Date] ) = 29 )
    )
)


[MAT Sales] := 
CALCULATE (
    [Sales], 
    FILTER (
        ALL ( 'Date' ), 
        'Date'[SequentialDayNumber] > MAX ( 'Date'[SequentialDayNumber] ) - 365
             && 'Date'[SequentialDayNumber] <= MAX ( 'Date'[SequentialDayNumber] )
    )
)


Period Comparison Pattern


[MOM Sales] := [Sales] – [PM Sales]
 
[MOM% Sales] := DIVIDE ( [MOM Sales], [PM Sales] )


More Pattern Examples
This section shows the time patterns for different types of calculations that you can apply to a custom monthly-based calendar without relying on DAX time intelligence functions. The measures defined will use the following naming convention:


Acronym | Description | Shift Period | Aggregation | Comparison
|----------|:-------------|:------:|:-------------:|------:|
YTD | Year To Date |  | X | 
QTD | Quarter To Date |  | X | 
MTD | Month To Date |  | X | 
MAT | Moving Annual Total |  | X | 
PY | Previous Year | X |  | 
PQ | Previous Quarter | X |  | 
PM | Previous Month | X |  | 
PP | Previous Period (automatically selects year, quarter, or month) | X |  | 
PMAT | Previous Year Moving Annual Total | X | X | 
YOY | Year Over Year |  |  | X
QOQ | Quarter Over Quarter |  |  | X
MOM | Month Over Month |  |  | X
POP | Period Over Period (automatically selects year, quarter, or month) |  |  | X
AOA | Moving Annual Total Over Moving Annual Total | X | X | 
PYTD | Previous Year To Date | X | X | 
PQTD | Previous Quarter To Date | X | X | 
PMTD | Previous Month To Date | X | X | 
YOYTD | Year Over Year To Date | X | X | X
QOQTD | Quarter Over Quarter To Date | X | X | X
MOMTD | Month Over Month To Date | X | X | X