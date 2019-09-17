# test

___
##### Basic Measures
* Total Amount:
  > TotalAmount = SUM(Sales[Amount])
*Total Quantity:
  > TotalQuantity = SUM(Sales[Quantity])
___
##### Day Measures
* Total Amount for Last Day (Yesterday)
  > Amount_LastDay = CALCULATE([TotalAmount],PREVIOUSDAY('Date'[Date]))
* Total Amount for same Day last Year
  > Amount_SameDayLastYear = CALCULATE([TotalAmount],SAMEPERIODLASTYEAR('Date'[Date]))
* Variance of total Amount compared to Total Amount for Last Day
  > Amount_DOD_Variance = [TotalAmount]-[Amount_LastDay]
* Variance % of total Amount compared to Total Amount for Last Day
  > Amount_DOD_Variance% = DIVIDE([Amount_DOD_Variance],[Amount_LastDay])
* Variance of total Amount compared to Total Amount for same Day last Year
  > Amount_YOY_Variance = [TotalAmount]-[Amount_SameDayLastYear]
* Variance % of total Amount compared to Total Amount same Day last Year
  > Amount_YOY_Variance% = DIVIDE([Amount_YOY_Variance],[Amount_LastDay])
* Total Quantity for Last Day (Yesterday)
  > Quantity_LastDay = CALCULATE([TotalQuantity],PREVIOUSDAY('Date'[Date]))
* Total Quantity for same Day last Year
  > Quantity_SameDayLastYear = CALCULATE([TotalQuantity],SAMEPERIODLASTYEAR('Date'[Date]))
* Variance of total Quantity compared to Total Quantity for Last Day
  > Quantity_DOD_Variance = [TotalQuantity]-[Quantity_LastDay]
* Variance % of total Quantity compared to Total Quantity for Last Day
  > Quantity_DOD_Variance% = DIVIDE([Quantity_DOD_Variance],[Quantity_LastDay])
* Variance of total Quantity compared to total Quantity for same Day last Year
  > Quantity_YOY_Variance = [TotalQuantity]-[Quantity_SameDayLastYear]
* Variance % of total Quantity compared to total Quantity for same Day last Year
  > Quantity_YOY_Variance% = DIVIDE([Quantity_YOY_Variance],[Quantity_LastDay])
___
##### Week Measures
* Total Amount Week To Date
  > Amount_WTD = IF (
  >     HASONEVALUE ( 'Date'[Year] )
  >         && HASONEVALUE ('Date'[WeekNumber] ), CALCULATE(
  >         [TotalAmount],
  >         FILTER (
  >             ALL ( 'Date' ),
  >             'Date'[Year] = VALUES ( 'Date'[Year] )
  >                 && 'Date'[WeekNumber] = VALUES ( 'Date'[WeekNumber] )
  >                 && 'Date'[Date] <= MAX ( 'Date'[Date] )
  >         )
  >     ))
* Total Amount for Last Week
  > Amount_LastWeek = SUMX(
  >     FILTER(ALL('Date'),
  >         IF(SELECTEDVALUE('Date'[WeekNumber])=1,
  >             'Date'[WeekNumber]=CALCULATE(MAX('Date'[WeekNumber]), ALL('Date')) && 'Date'[Year]=FORMAT(VALUE(SELECTEDVALUE('Date'[Year]))-1,""),
  >             'Date'[WeekNumber]=SELECTEDVALUE('Date'[WeekNumber])-1 && 'Date'[Year]=FORMAT(VALUE(SELECTEDVALUE('Date'[Year])),""))
  >     ),
  >     [TotalAmount])
* Total Amount for same Week Last Year
  > Amount_SameWeekLastYear = IF (
  >     HASONEVALUE ( 'Date'[Year] )
  >         && HASONEVALUE ('Date'[WeekNumber] ), CALCULATE(
  >         SUM ( Sales[Amount] ),
  >         FILTER (
  >             ALL ( 'Date' ),
  >             'Date'[Year] = FORMAT(VALUES ( 'Date'[Year] )-1,"")
  >                 && 'Date'[WeekNumber] = VALUES ( 'Date'[WeekNumber] )
  >                 && 'Date'[Date] <= MAX ( 'Date'[Date] )
  >         )
  >     ))
* Variance of total Amount Week To Date compared to Total Amount for Last Week
  > Amount_WTD_WOW_Variance = [Amount_WTD]-[Amount_LastWeek]
* Variance % of total Amount Week To Date compared to Total Amount for Last Week
  > Amount_WTD_WOW_Variance% = DIVIDE([Amount_WTD_WOW_Variance],[Amount_LastWeek])
* Variance of total Amount Week to Date compared to Total Amount for same Week last Year
  > Amount_WTD_YOY_Variance = [Amount_WTD]-[Amount_SameWeekLastYear]
* Variance % of total Amount Week to Date compared to Total Amount for same Week last Year
  > Amount_WTD_YOY_Variance% = DIVIDE([Amount_WTD_YOY_Variance],[Amount_SameWeekLastYear])
* Total Quantity Week To Date
  > Quantity_WTD = IF (
  >     HASONEVALUE ( 'Date'[Year] )
  >         && HASONEVALUE ('Date'[WeekNumber] ),
  >     CALCULATE (
  >         [TotalQuantity],
  >         FILTER (
  >             ALL ( 'Date' ),
  >             'Date'[Year] = VALUES ( 'Date'[Year] )
  >                 && 'Date'[WeekNumber] = VALUES ( 'Date'[WeekNumber] )
  >                 && 'Date'[Date] <= MAX ( 'Date'[Date] )
  >         )
  >     ),
  >     BLANK ()
  > )
* Total Quantity for same Week Last Year
  > Quantity_SameWeekLastYear = IF (
  >     HASONEVALUE ( 'Date'[Year] )
  >         && HASONEVALUE ('Date'[WeekNumber] ), CALCULATE(
  >         SUM ( Sales[Quantity] ),
  >         FILTER (
  >             ALL ( 'Date' ),
  >             'Date'[Year] = FORMAT(VALUES ( 'Date'[Year] )-1,"")
  >                 && 'Date'[WeekNumber] = VALUES ( 'Date'[WeekNumber] )
  >                 && 'Date'[Date] <= MAX ( 'Date'[Date] )
  >         )
  >     ))
* Total Quantity for Last Week
  > Quantity_LastWeek = SUMX(
  >     FILTER(ALL('Date'),
  >         IF(SELECTEDVALUE('Date'[WeekNumber])=1,
  >             'Date'[WeekNumber]=CALCULATE(MAX('Date'[WeekNumber]), ALL('Date')) && 'Date'[Year]=FORMAT(VALUE(SELECTEDVALUE('Date'[Year]))-1,""),
  >             'Date'[WeekNumber]=SELECTEDVALUE('Date'[WeekNumber])-1 && 'Date'[Year]=FORMAT(VALUE(SELECTEDVALUE('Date'[Year])),""))
  >     ),
  >     [TotalQuantity])
* Variance of total Quantity Week To Date compared to Total Quantity for Last Week
  > Quantity_WTD_WOW_Variance = [Quantity_WTD]-[Quantity_LastWeek]
* Variance % of total Quantity Week To Date compared to Total Quantity for Last Week
  > Quantity_WTD_WOW_Variance% = DIVIDE([Quantity_WTD_WOW_Variance],[Quantity_LastWeek])
* Variance of total Quantity Week to Date compared to Total Quantity for same Week last Year
  > Quantity_WTD_YOY_Variance = [Quantity_WTD]-[Quantity_SameWeekLastYear]
* Variance % of total Quantity Week to Date compared to Total Quantity for same Week last Year
  > Quantity_WTD_YOY_Variance% = DIVIDE([Quantity_WTD_YOY_Variance],[Quantity_SameWeekLastYear])
___
##### Month Measures
* Total Amount Month To Date
  > Amount_MTD = TOTALMTD([TotalAmount],'Date'[Date])
* Total Amount for same Month Last Year
  > Amount_SameMonthLastYear = CALCULATE([Amount_MTD],SAMEPERIODLASTYEAR('Date'[Date]))
* Total Amount for Last Month
  > Amount_LastMonth = CALCULATE([TotalAmount],PREVIOUSMONTH('Date'[Date]))
* Variance of total Amount Month To Date compared to Total Amount for Last Month
  > Amount_MTD_MOM_Variance = [Amount_MTD]-[Amount_LastMonth]
* Variance % of total Amount Month To Date compared to Total Amount for Last Month
  > Amount_MTD_MOM_Variance% = DIVIDE([Amount_MTD_MOM_Variance],[Amount_LastMonth])
* Variance of total Amount Month to Date compared to Total Amount for same Month last Year
  > Amount_MTD_YOY_Variance = [Amount_MTD]-[Amount_SameMonthLastYear]
* Variance % of total Amount Month to Date compared to Total Amount for same Month last Year
  > Amount_MTD_YOY_Variance% = DIVIDE([Amount_MTD_YOY_Variance],[Amount_SameMonthLastYear])
* Total Quantity Month To Date
  > Quantity_MTD = TOTALMTD([TotalQuantity],'Date'[Date])
* Total Quantity for same Month Last Year
  > Quantity_SameMonthLastYear = CALCULATE([Quantity_MTD],SAMEPERIODLASTYEAR('Date'[Date]))
* Total Quantity for Last Month
  > Quantity_LastMonth = CALCULATE([TotalQuantity],PREVIOUSMONTH('Date'[Date]))
* Variance of total Quantity Month To Date compared to Total Quantity for Last Month
  > Quantity_MTD_MOM_Variance = [Quantity_MTD]-[Quantity_LastMonth]
* Variance % of total Quantity Month To Date compared to Total Quantity for Last Month
  > Quantity_MTD_MOM_Variance% = DIVIDE([Quantity_MTD_MOM_Variance],[Quantity_LastMonth])
* Variance of total Quantity Month to Date compared to Total Quantity for same Month last Year
  > Quantity_MTD_YOY_Variance = [Quantity_MTD]-[Quantity_SameMonthLastYear]
* Variance % of total Quantity Month to Date compared to Total Quantity for same Month last Year
  > Quantity_MTD_YOY_Variance% = DIVIDE([Quantity_MTD_YOY_Variance],[Quantity_SameMonthLastYear])
___
##### Period Measures
* Total Amount Period To Date
  > Amount_PTD = IF (
  >     HASONEVALUE ( 'Date'[Year] )
  >         && HASONEVALUE ('Date'[TwoMonthPeriod] ),
  >     CALCULATE (
  >         [TotalAmount],
  >         FILTER (
  >             ALL ( 'Date' ),
  >             'Date'[Year] = VALUES ( 'Date'[Year] )
  >                 && 'Date'[TwoMonthPeriod] = VALUES ( 'Date'[TwoMonthPeriod] )
  >                 && 'Date'[Date] <= MAX ( 'Date'[Date] )
  >         )
  >     ),
  >     BLANK ()
  > )
* Total Amount for same Period Last Year
  > Amount_SamePeriodLastYear = CALCULATE([Amount_PTD],SAMEPERIODLASTYEAR('Date'[Date]))
* Total Amount for Last Period
  > Amount_LastPeriod = CALCULATE([TotalAmount],DATEADD('Date'[Date],-2,MONTH))
* Variance of total Amount Period To Date compared to Total Amount for Last Period
  > Amount_PTD_POP_Variance = [Amount_PTD]-[Amount_LastPeriod]
* Variance % of total Amount Period To Date compared to Total Amount for Last Period
  > Amount_PTD_POP_Variance% = DIVIDE([Amount_PTD_POP_Variance],[Amount_LastPeriod])
* Variance of total Amount Period to Date compared to Total Amount for same Period last Year
  > Amount_PTD_YOY_Variance = [Amount_PTD]-[Amount_SamePeriodLastYear]
* Variance % of total Amount Period to Date compared to Total Amount for same Period last Year
  > Amount_PTD_YOY_Variance% = DIVIDE([Amount_PTD_YOY_Variance],[Amount_SamePeriodLastYear])
* Total Quantity Period To Date
  > Quantity_PTD = IF (
  >     HASONEVALUE ( 'Date'[Year] )
  >         && HASONEVALUE ('Date'[TwoMonthPeriod] ),
  >     CALCULATE (
  >         [TotalQuantity],
  >         FILTER (
  >             ALL ( 'Date' ),
  >             'Date'[Year] = VALUES ( 'Date'[Year] )
  >                 && 'Date'[TwoMonthPeriod] = VALUES ( 'Date'[TwoMonthPeriod] )
  >                 && 'Date'[Date] <= MAX ( 'Date'[Date] )
  >         )
  >     ),
  >     BLANK ()
  > )
* Total Quantity for same Period Last Year
  > Quantity_SamePeriodLastYear = CALCULATE([Quantity_PTD],SAMEPERIODLASTYEAR('Date'[Date]))
* Total Quantity for Last Period
  > Quantity_LastPeriod = CALCULATE([TotalQuantity],DATEADD('Date'[Date],-2,MONTH))
* Variance of total Quantity Period To Date compared to Total Quantity for Last Period
  > Quantity_PTD_POP_Variance = [Quantity_PTD]-[Quantity_LastPeriod]
* Variance % of total Quantity Period To Date compared to Total Quantity for Last Period
  > Quantity_PTD_POP_Variance% = DIVIDE([Quantity_PTD_POP_Variance],[Quantity_LastPeriod])
* Variance % of total Quantity Period to Date compared to Total Quantity for same Period last Year
  > Quantity_PTD_YOY_Variance = [Quantity_PTD]-[Quantity_SamePeriodLastYear]
* Variance of total Quantity Period to Date compared to Total Quantity for same Period last Year
  > Quantity_PTD_YOY_Variance% = DIVIDE([Quantity_PTD_YOY_Variance],[Quantity_SamePeriodLastYear])
___
##### Quarter Measures
* Total Amount Quarter To Date
  > Amount_QTD = TOTALQTD([TotalAmount],'Date'[Date])
* Total Amount for same Quarter Last Year
  > Amount_SameQuarterLastYear = CALCULATE([Amount_QTD],SAMEPERIODLASTYEAR('Date'[Date]))
* Total Amount for Last Quarter
  > Amount_LastQuarter = CALCULATE([TotalAmount],PREVIOUSQUARTER('Date'[Date]))
* Variance of total Amount Quarter To Date compared to Total Amount for Last Quarter
  > Amount_QTD_QOQ_Variance = [Amount_QTD]-[Amount_LastQuarter]
* Variance % of total Amount Quarter To Date compared to Total Amount for Last Quarter
  > Amount_QTD_QOQ_Variance% = DIVIDE([Amount_QTD_QOQ_Variance],[Amount_LastQuarter])
* Variance of total Amount Quarter to Date compared to Total Amount for same Quarter last Year
  > Amount_QTD_YOY_Variance = [Amount_QTD]-[Amount_SameQuarterLastYear]
* Variance % of total Amount Quarter to Date compared to Total Amount for same Quarter last Year
  > Amount_QTD_YOY_Variance% = DIVIDE([Amount_QTD_YOY_Variance],[Amount_SameQuarterLastYear])
* Total Quantity Quarter To Date
  > Quantity_QTD = TOTALQTD([TotalQuantity],'Date'[Date])
* Total Quantity for same Quarter Last Year
  > Quantity_SameQuarterLastYear = CALCULATE([Quantity_QTD],SAMEPERIODLASTYEAR('Date'[Date]))
* Total Quantity for Last Quarter
  > Quantity_LastQuarter = CALCULATE([TotalQuantity],PREVIOUSQUARTER('Date'[Date]))
* Variance of total Quantity Quarter To Date compared to Total Quantity for Last Quarter
  > Quantity_QTD_QOQ_Variance = [Quantity_QTD]-[Quantity_LastQuarter]
* Variance % of total Quantity Quarter To Date compared to Total Quantity for Last Quarter
  > Quantity_QTD_QOQ_Variance% = DIVIDE([Quantity_QTD_QOQ_Variance],[Quantity_LastQuarter])
* Variance of total Quantity Quarter To Date compared to Total Quantity or same Quarter last Year
  > Quantity_QTD_YOY_Variance = [Quantity_QTD]-[Quantity_SameQuarterLastYear]
* Variance % of total Quantity Quarter To Date compared to Total Quantity for same Quarter last Year
  > Quantity_QTD_YOY_Variance% = DIVIDE([Quantity_QTD_YOY_Variance],[Quantity_SameQuarterLastYear])
___
##### Year Measures
* Total Amount Year To Date
  > Amount_YTD = TOTALYTD([TotalAmount],'Date'[Date])
* Total Amount for Last Year
  > Amount_LastYear = CALCULATE([Amount_YTD],PREVIOUSYEAR('Date'[Date]))
* Variance of total Amount Year To Date compared to Total Amount for Last Year
  > Amount_YTD_YOY_Variance = [Amount_YTD]-[Amount_LastYear]
* Variance% of total Amount Year To Date compared to Total Amount for Last Year
  > Amount_YTD_YOY_Variance% = DIVIDE([Amount_YTD_YOY_Variance],[Amount_LastYear])
* Total Quantity Year To Date
  > Quantity_YTD = TOTALYTD([TotalQuantity],'Date'[Date])
* Total Quantity for Last Year
  > Quantity_LastYear = CALCULATE([TotalQuantity],PREVIOUSYEAR('Date'[Date]))
* Variance of total Quantity Year To Date compared to Total Quantity for Last Year
  > Quantity_YTD_YOY_Variance = -[Quantity_YTD]-[Quantity_LastYear]
* Variance% of total Quantity Year To Date compared to Total Quantity for Last Year
  > Quantity_YTD_YOY_Variance% = DIVIDE([Quantity_YTD_YOY_Variance],[Quantity_LastYear])

=>> EOF