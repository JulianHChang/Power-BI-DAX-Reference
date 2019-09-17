# power-bi-dax-reference
Data Analysis Expressions (DAX) is a library of functions and operators that can be combined to build formulas and expressions in Power BI Desktop, Azure Analysis Services, SQL Server Analysis Services, and Power Pivot in Excel.
\
<img src="images/jhc_powerbicertificate.png" width=80%>
\
## Link: [EDX VERIFIED CERTIFICATE of ACHIEVEMENT](courses.edx.org/certificates/21b3a1602bff44e78246bd5467984a0a)

---
# Data Analysis Expressions
### DAX is a formula language. DAX formulas can be used to define calculated columns in a table and they can also be used to define measures (also known as calculated fields).



Calculated columns are just like in Excel – you enter a formula, and that formula is evaluated for each row in the table, effectively filling in the entire column with values.  

A measure is different. When you define a measure, you provide a DAX formula and a name. This measure can be placed onto an Excel PivotTable, and it will be evaluated many times, once for each cell in the values area of that PivotTable.

## Calculated Columns
– Used to add an additional column to data table  
– Can be a column added from a related table (like a
VLOOKUP) or new data, derived from existing data  
– Column can be used in any area of the pivot

## Calculated Fields  
– Used to add a calculated element  
– Aggregate function that applies to whole table, column, or range  
– Something that needs to be recalculated
– Fields can only be used in the VALUES section

## Row context
• The one row being evaluated  
• Automatic for calculated columns  
• Can be created in other ways as well (SUMX, AVERAGEX, etc.)
<img src="images/row_context.png">

## Filter context  
• The filters being applied by the pivot table  
• Filters can be explicit or implicit  
• Can add additional filters only with CALCULATE
<img src="images/filter_context.png">

## Relationships and Filter Context



## Measures and Filter Context




## Resources
DAX Studio [link](https://daxstudio.org)  
DAX Formatter [link](https://www.daxformatter.com/)