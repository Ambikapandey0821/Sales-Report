# Sales-Dashboard

# Dashboard Link : 

https://app.powerbi.com/links/e1plsW6XTr?ctid=9bb2360a-034c-4ecf-8228-aafe1a12b953&pbi_source=linkShare&bookmarkGuid=4faf1200-1fde-477e-b561-99254b9d694e

# Problem Statement

The objective of the sales dashboard report is to provide a comprehensive overview of our organization's sales performance, trends 
and key metrics in order to facilitate data-driven decision-making and improve overall sales effectiveness.
This report will enable stakeholders to quickly and easily identify areas of strength and opportunities for improvement, ultimately driving increased revenue and profitability for the business.

# Steps Followed

Step 1 : Load data into Power BI Desktop, dataset is a csv file.

Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.

Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".

Step 4 : It was observed that in none of the columns errors & empty values were present.

Step 5 :In the report view, under the view tab, theme was selected.

Step 7 : A New Calender table created using with reference to Order date. Along with Other Columns like

        Calender Table = (CALENDAR(MIN(Orders[Order Date]),MAX((Orders[Order Date]))))
        Month = FORMAT('Calender Table'[Date],"MMMM")
        Year = FORMAT('Calender Table'[Date],"YYYY")
        Month No = FORMAT('Calender Table'[Date],"MM")

Step 8 : In this step in Model view, Relationship has been establised between the tables using common columns and one to many cardinality.

Step 9 : Another Table created with the name of All Measures where all the measures are created.

        ![image](https://github.com/Ambikapandey0821/Sales-Report/assets/162020155/b29ac4ad-456a-44e6-8ccf-10073c66d0b5)


Step 10 : A Measure Created to calculate the total Revenue.

        Total Revenue = SUM(Orders[Sales])
        
![image](https://github.com/Ambikapandey0821/Sales-Report/assets/162020155/f5be54a6-ba42-4d96-ad30-0601078bda4c)

Step 10 : A Measure Created to calculate the total Profit.

        Total Profit = SUM(Orders[Profit])
        
![image](https://github.com/Ambikapandey0821/Sales-Report/assets/162020155/0e6cccac-ae19-4598-8eb9-7dcd5902aff7)

Step 10 : A Measure Created to calculate the total Orders.

        Total Orders = COUNT(Orders[Order ID])
        
![image](https://github.com/Ambikapandey0821/Sales-Report/assets/162020155/04e0deb5-ac6c-484c-b2a0-7380f7f90ef2)

Step 10 : 2 Measure Created to calculate the rank of the states based on Revenue generation and then to select top 5 states.

        States Ranking = RANKX(ALL(Orders[State]),CALCULATE(SUM(Orders[Sales])),,DESC,Dense)
        
        Top 5 States = IF([States Ranking]<=5,SUM(Orders[Sales]),BLANK())
        
![image](https://github.com/Ambikapandey0821/Sales-Report/assets/162020155/dc637ac3-696c-47cb-bc5a-b5efb38c5d7a)

Step 10 : 2 Measure Created to calculate the YOY Revenue Growth,YOY Order Growth and to make the font color dynaminc another 2 measure created to make the values color dynamic.

        YoY Sales Growth = VAR _premonthsales = CALCULATE(SUM(Orders[Sales]),DATEADD('Calender Table'[Date],-1,YEAR))
        var _blank=IF(_premonthsales=BLANK(),[Total Revenue],_premonthsales)
        var _salesgrowth = DIVIDE([Total Revenue]-_blank,_blank)
        RETURN _salesgrowth

        YoY Orders Growth = Var _totalorders=COUNT(Orders[Order ID])
        VAR _premonthorder = CALCULATE(COUNT(Orders[Customer ID]),DATEADD('Calender Table'[Date],-1,YEAR))
        var _blank= IF(_premonthorder=BLANK(),[Total Orders],_premonthorder)
        var _ordergrowth = DIVIDE(_totalorders-_blank,_blank)
        RETURN _ordergrowth

        YOY Sales color = IF([YoY Sales Growth]=0,"#1D2DE6",if([YoY Sales Growth]>0,"green","red"))

        YOY Order color = IF([YoY Orders Growth]=0,"#1D2DE6",if([YoY Orders Growth]>0,"green","red"))
        
![image](https://github.com/Ambikapandey0821/Sales-Report/assets/162020155/a37d191f-26ee-443f-9997-1fa4b0cfd775)

Step 18 : A slicer Added so that Page can be filtered on the basis of years.

![image](https://github.com/Ambikapandey0821/Sales-Report/assets/162020155/c7d0c1c2-5630-4a2f-9c48-83680e468af1)

Step 18 : Report Published in the Power BI Services.

![image](https://github.com/Ambikapandey0821/Sales-Report/assets/162020155/9272fd29-7f2d-437f-a207-040c8fe2308c)

# Insights

Following inferences can be drawn from the Dashboard;

Highest Revenue Genereated in 2017

Highest Profit Genereated in 2017

Highest Orders received in 2017

# States -
Top States  with highest revenue in consistently in all the Years

- California
- New York
- Texas
We can say that these thee states are the states that generates the highest revenue and profit.

# Month -
Month with Higest Revenue and Profit across all the Years

- December 
We can say that on sales and profit increases in the last 2 quarter of the Calender Year.

# Category -
Category with Highest to lowest Revenue and profits generation.

- Technology
- Funiture
- Office Supplies
We can say that Category Technology has been generating the highest revenue and profit across all the years, and Office Supplies Lowest.

# Segment -
Segment with Highest to lowest Revenue and Profits generation.

- Consumer
- Corporate
- Home Office
We can say that Consumer Segment has been generating the highest revenue and profit across all the years. And Office Supplies Lowest.



        
