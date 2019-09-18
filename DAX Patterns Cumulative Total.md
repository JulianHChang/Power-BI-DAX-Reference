# Cumulative Total


[Link](daxpatterns.com/cumulative-total/)  



Basic Pattern Example


Cumulative Quantity :=  
CALCULATE (  
    SUM ( Transactions[Quantity] ),  
    FILTER (  
        ALL ( 'Date'[Date] ),  
        'Date'[Date] <= MAX ( 'Date'[Date] )  
    )  
)  

Complete Pattern


Cumulative Quantity :=
IF (
    MIN ( 'Date'[DateKey] )
        <= CALCULATE ( MAX ( Transactions[DateKey] ), ALL ( Transactions ) ),
    CALCULATE (
        SUM ( Transactions[Quantity] ),
        FILTER (
            ALL ( 'Date'[Date] ),
            'Date'[Date] <= MAX ( 'Date'[Date] )
        )
    )
)
  
  
Cumulative Quantity Unchecked :=
CALCULATE (
    SUM ( Transactions[Quantity] ),
    FILTER (
        ALL ( 'Date'[Date] ),
        'Date'[Date] <= MAX ( 'Date'[Date] )
    )
)
