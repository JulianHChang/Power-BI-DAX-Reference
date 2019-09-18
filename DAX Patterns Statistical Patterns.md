# Statistical Patterns

[LInk](https://www.daxpatterns.com/statistical-patterns/)

Basic Pattern Example
Average
You can use standard DAX functions to calculate the mean (arithmetic average) of a set of values.

- AVERAGE: returns the average of all the numbers in a numeric column.
- AVERAGEA: returns the average of all the numbers in a column, handling both text and non-numeric values (non-numeric and empty text values count as 0).
- AVERAGEX: calculate the average on an expression evaluated over a table.


Moving Average

Moving AverageX 7 Days :=
AVERAGEX (
    DATESINPERIOD (
        'Date'[Date],
        LASTDATE ( 'Date'[Date] ),
        -7,
        DAY
    ),
    [Total Amount]
)


Median

Median :=
(
    MINX (
        FILTER (
            VALUES ( Data[Value] ),
            CALCULATE (
                COUNT ( Data[Value] ),
                Data[Value]
                    <= EARLIER ( Data[Value] )
            )
                > COUNT ( Data[Value] ) / 2
        ),
        Data[Value]
    )
        + MINX (
            FILTER (
                VALUES ( Data[Value] ),
                CALCULATE (
                    COUNT ( Data[Value] ),
                    Data[Value]
                        <= EARLIER ( Data[Value] )
                )
                    > ( COUNT ( Data[Value] ) - 1 ) / 2
            ),
            Data[Value]
        )
) / 2



Complete Pattern


Moving AverageX <number_of_days> Days:=
AVERAGEX (
    FILTER (
        ALL ( <date_column> ),
        <date_column> > ( MAX ( <date_column> ) - <number_of_days> )
            && <date_column> <= MAX ( <date_column> )
    ),
    <measure>
)



Moving Average <number_of_days> Days:=
CALCULATE (
    IF (
        COUNT ( <date_column> ) >= <number_of_days>,
        SUM ( Sales[Amount] ) / COUNT ( <date_column> )
    ),
    FILTER (
        ALL ( <date_column> ),
        <date_column> > ( MAX ( <date_column> ) - <number_of_days> )
            && <date_column> <= MAX ( <date_column> )
    )
)



Moving Average <number_of_days> Days No Zero:=
CALCULATE (
    IF (
        COUNT ( <date_column> ) >= <number_of_days>,
        SUM ( Sales[Amount] ) / CALCULATE ( COUNT ( <date_column> ), <fact_table> )
    ),
    FILTER (
        ALL ( <date_column> ),
        <date_column> > ( MAX ( <date_column> ) - <number_of_days> )
            && <date_column> <= MAX ( <date_column> )
    )
)

Moving Average 7 Days :=
CALCULATE (
    IF (
        COUNT ( 'Date'[Date] ) >= 7,
        SUM ( Sales[Amount] ) / COUNT ( 'Date'[Date] )
    ),
    FILTER (
        ALL ( 'Date'[Date] ),
        'Date'[Date] > ( MAX ( 'Date'[Date] ) - 7 )
            && 'Date'[Date] <= MAX ( 'Date'[Date] )     ) )




Moving Average 7 Days No Zero :=
CALCULATE (
    IF (
        COUNT ( 'Date'[Date] ) >= 7,
        SUM ( Sales[Amount] ) / CALCULATE ( COUNT ( 'Date'[Date] ), Sales )
    ),
    FILTER (
        ALL ( 'Date'[Date] ),
        'Date'[Date] > ( MAX ( 'Date'[Date] ) - 7 )
            && 'Date'[Date] <= MAX ( 'Date'[Date] )
    )
)