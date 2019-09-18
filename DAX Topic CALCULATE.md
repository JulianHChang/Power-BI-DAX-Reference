## CALCULATE() with a Single Table 
[Total Male Customers] = CALCULATE([Total number of Customers], Customers[Gender] = "M")  
[Total Customers Born Before 1950] = CALCULATE([Total number of Customers], Customers[BirthDate] <DATE(1950,1,1))  
[Total Customers Born in January] = CALCULATE([Total number of Customers], MONTH(Customers[BirthDate])=1)  
[Customers Earning at Least $100,000 per Year] = CALCULATE([Total number of Customers], Customers[YearlyIncome]>=100000)  

## CALCULATE() with Multiple Tables 
[Total Sales of Clothing] = CALCULATE([Total Sales Amount], Products[Category]="Clothing")  
[Sales to Female Customers] = CALCULATE([Total Sales Amount], Customers[Gender]="F")  
[Sales of Bikes to Married Men] = CALCULATE([Total Sales Amount], Customers[MaritalStatus]="M", Customers[Gender]="M", Products[Category]="Bikes")  