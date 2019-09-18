# Aggregation functions, or Aggregators

All the functions in this section are aggregation functions, or aggregators. That is, they take inputs from a column or table and somehow aggregate the contents (differently for each formula). 

Most of the DAX functions in this section accept a column as the only parameter, like this: =FORMULA(ColumnName). The only exception is =COUNTROWS(Table), which takes a table (not a column) as the parameter.



## SUM()
[Total Sales Amount] = SUM(Sales[ExtendedAmount])  
or [Total Sales Amount] = SUM(Sales[SalesAmount])  
[Total Cost Value] = SUM(Sales[TotalProductCost])  
or [Total Cost Value] = SUM(Sales[ProductStandardCost])  
[Total Margin $]= [Total Sales Value] – [Total Cost Value]  
[Total Margin %] = [Total Margin $] / [Total Sales Value]  
or [Total Margin %] = DIVIDE([Total Margin $] , [Total Sales Value])  
[Total Sales Tax Paid] = SUM(Sales[SalesTax])  
[Total Sales Including Tax]= [Total Sales Value] + [Total Sales Tax]  
[Total Order Quantity] = SUM(Sales[OrderQuantity])  
## COUNT()
[Total Number of Products] = COUNT(Products[ProductKey])  
[Total Number of Customers]= COUNT(Customers[CustomerKey])  
Note Counting the "key" columns is generally pretty safe because, by definition, each one must have a value. Technically, you can count any column that has a numeric value in each cell, and you will get the same answer. Just be careful if you are counting a numeric column that may have blank values: COUNT()will not count blanks.
## COUNTROWS()
Note Remember that COUNTROWS() takes a table, not a column, as input
[Total Number of Products COUNTROWS Version] = COUNTROWS(Products)  
[Total Number of Customers COUNTROWS Version] = COUNTROWS(Customers)  
## DISTINCTCOUNT()
[Total Customers in Database Distinctcount Version]= DISTINCTCOUNT(Customers[CustomerKey])  
[Count of Occupation]= DISTINCTCOUNT(Customers[Occupation])  
[Count of Country] = DISTINCTCOUNT(Territories[Country])  
[Customers That Have Purchased]= DISTINCTCOUNT(Sales[CustomerKey])  
## MAX(), MIN(), and AVERAGE()
[Maximum Tax Paid on a Product] = MAX(Sales[TaxAmt])  
[Minimum Price Paid for a Product]= MIN(Sales[ExtendedAmount])  
[Average Price Paid for a Product]= AVERAGE(Sales[ExtendedAmount])  
## COUNTBLANK()
[Customers Without Address Line 2]= COUNTBLANK(Customers[AddressLine2])  
[Products Without Weight Values]= COUNTBLANK(Products[Weight])  
## DIVIDE()
[Margin %]= DIVIDE([Total Margin $] , [Total Sales Amount] )  
[Markup %] = DIVIDE([Total Margin $] , [Total Cost Value])  
[Tax %] = DIVIDE(SUM(Sales[TaxAmt]) , [Total Sales Amount])  
