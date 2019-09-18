## FILTER() 


The syntax of FILTER() is as follows:  
= FILTER(Table , myFilter)  
Table is any table (or function that returns a table, such as ALL()), and myFilter is any expression that evaluates to a TRUE/FALSE answer.



[Total Sales of Products That Have Some Sales but Less Than $10,000] = CALCULATE([Total Sales Amount], FILTER(Products, [Total Sales Amount] <=10000 && [Total Sales Amount] >0))  
[Count of Products That Have Some Sales but Less Than $10,000] = CALCULATE(COUNTROWS(Products), FILTER(Products, [Total Sales Amount]  