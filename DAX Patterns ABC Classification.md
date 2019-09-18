# ABC Classification

[Link](daxpatterns.com/abc-classification/)


Basic Pattern Example


[ProductSales] =
CALCULATE ( SUM ( Sales[SalesAmount] ) )
 
[CumulatedSales] = 
CALCULATE (
    SUM ( Products[ProductSales] ),
    ALL ( Products ),
    Products[ProductSales] >= EARLIER ( Products[ProductSales] )
)
 
[CumulatedPercentage] =
Products[CumulatedSales] / SUM ( Products[ProductSales] )
 
[ABC Class] =
SWITCH (
    TRUE (),
    Products[CumulatedPercentage] <= 0.7, "A",
    Products[CumulatedPercentage] <= 0.9, "B",
    "C"
)



Complete Pattern


[EntityMeasure] =
CALCULATE ( <measure> )
 
[CumulatedPercentage] =
CALCULATE (
    <measure>,
    ALL ( <granularity_table> ),
    <granularity_table>[EntityMeasure]
        >= EARLIER ( <granularity_table>[EntityMeasure] )
)
    / CALCULATE ( <measure>, ALL ( <granularity_table> ) )
 
[ABC Class] =
SWITCH (
    TRUE (),
    <granularity_table>[CumulatedPercentage] <= 0.7, "A",
    <granularity_table>[CumulatedPercentage] <= 0.9, "B",
    "C"
)



[ProductSales] =
CALCULATE ( [Sales Amount] )
 
[ProductPercentage] =
CALCULATE (
    [Sales Amount],
    ALL ( Products ),
    Products[ProductSales] >= EARLIER ( Products[ProductSales] )
)
    / CALCULATE ( [Sales Amount], ALL ( Products ) )
 
[ABC Product] =
SWITCH (
    TRUE (),
    Products[ProductPercentage] <= 0.7, "A",
    Products[ProductPercentage] <= 0.9, "B",
    "C"
)



[EntityMeasure] =
CALCULATE (
    <measure>,
    ALL ( <granularity_table> ),
    <granularity_table>[<granularity_attribute>] 
        = EARLIER( <granularity_table>[<granularity_attribute>] )
)



[ModelSales] =
CALCULATE (
    [Sales Amount],
    ALL ( Products ),
    Products[ProductModel] = EARLIER ( Products[ProductModel] )
)
 
[ModelPercentage] =
CALCULATE (
    [Sales Amount],
    ALL ( Products ),
    Products[ModelSales] >= EARLIER ( Products[ModelSales] )
)
    / CALCULATE ( [Sales Amount], ALL ( Products ) )
 
[ABC Model] =
SWITCH (
    TRUE (),
    Products[ModelPercentage] <= 0.7, "A",
    Products[ModelPercentage] <= 0.9, "B",
    "C"
)

[EntityMeasure] =
CALCULATE (
    <measure>,
    ALLEXCEPT ( <granularity_table>, <granularity_table>[<granularity_attribute>] )
)



[ProductSales] =
CALCULATE (
    [Sales Amount],
    ALLEXCEPT ( Sales, Sales[Product] )
)
 
[ProductPercentage] =
CALCULATE (
    [Sales Amount],
    ALL ( Sales ),
    Sales[ProductSales]
        >= EARLIER ( Sales[ProductSales] )
)
    / CALCULATE ( [Sales Amount], ALL ( Sales ) )
 
[ABC Product] =
SWITCH (
    TRUE,
    Sales[ProductPercentage] <= 0.7, "A",
    Sales[ProductPercentage] <= 0.9, "B",
    "C"
)
 
[ModelSales] =
CALCULATE (
    [Sales Amount],
    ALLEXCEPT ( Sales, Sales[Model] )
)
 
[ModelPercentage] =
CALCULATE (
    [Sales Amount],
    ALL ( Sales ),
    Sales[ModelSales]
        >= EARLIER ( Sales[ModelSales] )
)
    / CALCULATE ( [Sales Amount], ALL ( Sales ) )
 
[ABC Model] =
SWITCH (
    TRUE (),
    Products[ModelPercentage] <= 0.7, "A",
    Products[ModelPercentage] <= 0.9, "B",
    "C"
)