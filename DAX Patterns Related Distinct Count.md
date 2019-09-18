# Related Distinct Count

[Link](https://www.daxpatterns.com/distinct-count/)



Basic Pattern Example


SoldProducts := DISTINCTCOUNT ( Sales[ProductKey] )
 
SoldCategories :=
CALCULATE (
    DISTINCTCOUNT ( Products[CategoryName] ),
    Sales
)


ListProducts := DISTINCTCOUNT ( Products[ProductKey] )
 
ListCategories := DISTINCTCOUNT ( Products[CategoryName] )


Complete Pattern



SoldSubcategories := 
CALCULATE (
    DISTINCTCOUNT ( Products[SubcategoryKey] ),
    Sales 
)
 
SoldCategories := 
CALCULATE (
    DISTINCTCOUNT( Subcategories[CategoryName] ), 
    Sales 
)


SoldProducts := DISTINCTCOUNT ( Sales[ProductKey] )
 
DaysWithSales := DISTINCTCOUNT ( Sales[Date] )



SoldProducts := 
CALCULATE (
    DISTINCTCOUNT ( Sales[ProductKey] ),
    Sales
)
 
DaysWithSales := 
CALCULATE (
    DISTINCTCOUNT ( Sales[Date] ),
    Sales
)


Distinct Count on Attribute in a Star Schema


MonthsWithSales := 
CALCULATE (
    DISTINCTCOUNT ( Dates[MonthNumber] ),
    Sales 
)
 
SoldSubcategories := 
CALCULATE (
    DISTINCTCOUNT ( Products[SubcategoryKey] ),
    Sales 
)



Distinct Count on Attribute in a Snowflake Schema


SoldCategories := 
CALCULATE (
    DISTINCTCOUNT ( Subcategories[CategoryName] ),
    Sales 
)


WrongCalculation := 
CALCULATE (
    DISTINCTCOUNT ( Subcategories[CategoryName] ),
    Products 
)

