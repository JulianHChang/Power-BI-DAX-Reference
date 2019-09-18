## ALL(), ALLEXCEPT(), and ALLSELECTED() 
[Total Sales to All Customers] = CALCULATE([Total Sales Amount] , All(Customers))  
Note This calculated field belongs in the Sales table, not the Customers table.  
[% of All Customer Sales] = DIVIDE([Total Sales Amount] , [Total Sales to All Customers])  
[Total Sales to Selected Customers] = CALCULATE([Total Sales Amount] , ALLSELECTED(Customers))  
[% of Sales to Selected Customers] = DIVIDE([Total Sales Amount] , [Total Sales to Selected Customers])  
[Total Sales for All Days Selected Dates] = CALCULATE([Total Sales Amount] , ALLSELECTED(Calendar)) Note Did you know to use ALLSELECTED() and not ALLEXCEPT()?  
[% Sales for All Days Selected Dates] = DIVIDE([Total Sales Amount] , [Total Sales for All Days Selected Dates]) This is what your pivot table should look like:  
[Total Orders All Customers] = CALCULATE([Total Order Quantity] , ALL(Customers))  
[Baseline Orders for All Customers with This Occupation] = CALCULATE([Total Order Quantity] , ALLEXCEPT(Customers, Customers[Occupation]))  
[Baseline % This Occupation of All Customer Orders] = DIVIDE([Baseline Orders for All customers with this Occupation] , [Total Orders All Customers])  
[Total Orders Selected Customers] = CALCULATE([Total Order Quantity] , ALLSELECTED(Customers])  
[Occupation % of Selected Customers] = DIVIDE([Total Order Quantity] , [Total Orders Selected Customers])  
[Percentage Point Variation to Baseline] = [Occupation % of Selected Customers] - [Baseline % this Occupation is of All Customer Orders]  
