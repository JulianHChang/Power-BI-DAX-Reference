## VALUES()  
[Number of Color Variants] = COUNTROWS(VALUES(Products[Color]))  
[Number of Sub Categories] = COUNTROWS(VALUES(Products[SubCategory]))  
[Number of Size Ranges] = COUNTROWS(VALUES(Products[SizeRange]))  
[Product Category (Values)] = IF(HASONEVALUE(Products[Category]), VALUES(Products[Category]) )  
[Product Subcategory (Values)] = IF(HASONEVALUE(Products[SubCategory]), VALUES(Products[SubCategory]) )  
[Product Color (Values)] = IF(HASONEVALUE(Products[color]), VALUES(Products[color]) )  
[Product Subcategory (Values) edited] = IF(HASONEVALUE(Products[SubCategory]), VALUES(Products[SubCategory]),"More than 1 Sub Cat" )  
[Product Color (Values) edited] = IF(HASONEVALUE(Products[color]), VALUES(Products[color]),"More than 1 Color" )  