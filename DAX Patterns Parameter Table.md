# Parameter Table

[Link](https://www.daxpatterns.com/parameter-table/)


Basic Pattern Example

Sales Amount :=
IF (
    HASONEVALUE ( Scale[Scale] ),
    SUM ( Sales[SalesAmount] ) / VALUES ( Scale[Scale] ),
    SUM ( Sales[SalesAmount] )
)


Complete Pattern


ParameterSelection :=
IF (
    HASONEVALUE ( Parameter[ParameterValue] ),
    "Selection: " & VALUES ( Parameter[ParameterValue] ),
    IF (
        NOT ( ISFILTERED ( Parameter[ParameterDescription] ) ),
        "No Selection",
        "Multiple Selection"
    )
)


Using a Single Parameter Table


SalesAmount := SUMX ( Sales, Sales[Quantity] * Sales[Price] )


DiscountedSalesAmount :=
IF (
    HASONEVALUE ( Discounts[DiscountValue] ),
    [SalesAmount] * ( 1 – VALUES ( Discounts[DiscountValue] ) ),
    IF (
        NOT ( ISFILTERED ( Discounts[Discount] ) ),
        [SalesAmount],
        BLANK ()
    )
)



Handling More Parameter Tables


SUMX (
    Sales,
    [SalesAmount]
    * IF (
         Sales[Quantity] >= VALUES ( MinQuantity[MinQuantity] ),
         1 – VALUES ( Discounts[DiscountValue] ),
         1
      )
)
  
 
 
CALCULATE (
    [SalesAmount] * ( 1 – VALUES ( Discounts[DiscountValue] ) ),
    Sales[Quantity] >= VALUES ( MinQuantity[MinQuantity] )
) + CALCULATE (
    [SalesAmount],
    Sales[Quantity] < VALUES ( MinQuantity[MinQuantity] )
)

 
DiscountedSalesAmount :=
IF (
    HASONEVALUE ( Discounts[DiscountValue] ) && HASONEVALUE ( MinQuantity[MinQuantity] ),
    CALCULATE (
        [SalesAmount] * ( 1 – VALUES ( Discounts[DiscountValue] ) ),
        Sales[Quantity] >= VALUES ( MinQuantity[MinQuantity] )
    )
    + CALCULATE (
        [SalesAmount],
        Sales[Quantity] < VALUES ( MinQuantity[MinQuantity] )
    ),
    IF (
        NOT ( ISFILTERED ( Discounts[Discount] ) )
            && NOT ( ISFILTERED ( MinQuantity[MinQuantity] ) ),
        [SalesAmount],
        IF (
            HASONEVALUE ( Discounts[Discount] )
                && NOT ( ISFILTERED ( MinQuantity[MinQuantity] ) ) ,
            CALCULATE ( [SalesAmount] * ( 1 – VALUES ( Discounts[DiscountValue] ) ) ),
            BLANK ()
        )
    )
)