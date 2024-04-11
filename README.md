# Sales-Report

Dashboard Link : https://app.powerbi.com/links/e1plsW6XTr?ctid=9bb2360a-034c-4ecf-8228-aafe1a12b953&pbi_source=linkShare&bookmarkGuid=4faf1200-1fde-477e-b561-99254b9d694e

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

Step 8 : Another Table created with the name of All Measures where all the measures are created.

Step 9 : 

Step 10 : 
