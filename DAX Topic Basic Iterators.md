
## SUMX()
[Total Sales SUMX Version]= SUMX(Sales, Sales[OrderQuantity] * Sales[UnitPrice])  
Note In this sample database, the order quantity is always 1
[Total Sales Including Tax SUMX Version]= SUMX(Sales,Sales[ExtendedAmount] + Sales[TaxAmt])  
[Total Sales Including Freight]= SUMX(Sales,Sales[ExtendedAmount] + Sales[Freight])  
[Dealer Margin] = SUMX (Products,Products[ListPrice] - Products[DealerPrice])  


## AVERAGEX()
[Average Sell Price per Item] = AVERAGEX(Sales, Sales[OrderQuantity] * Sales[UnitPrice])  
[Average Tax Paid] = AVERAGEX(Sales, Sales[TaxAmt])  
Note how the expression can be a single column. It doesn't have to be an equation using multiple columns.  
[Average Safety Stock] = AVERAGEX(Products,Products[SafetyStockLevel])  

MINX  
MAXX  
COUNTX  
COUNTAX  
PRODUCTX  
CONCATENATEX  
RANKX  