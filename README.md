# S&P 500 Stock Prices
A Power BI project that examine movement of various stock price for the period between 2014 to 2017, and how well the different stock perform in the time under review using single day of trading 

## Project overview ##
This project aims to provide the s & p 500 stock companies with the required understanding trend path over the year under review, derived from the analysis of sales, volume and date of transaction using Power BI. By understanding historical sales trends, product performance, key customer relationships, and stock market volatility, the company can make informed decisions to optimize its business strategies, improve operational efficiency, and enhance overall performance in the stock market environment.
The project will hope to provide the needed answer to the various question boarding on trend path and help the management to come out with needed strategies which are available for growth.

## Project Scope ## 
This project covers stock market data of daily transaction for the year between 2014 to 2017 focusing on volume of stock sold and the price variation during the period under review, product performance, sales trends, and frequency of sales and consistency.

## Business Objective ##
The purpose for this analysis is to identify if there are any noticeable sales trends over time, to find out the best and the worst selling stock by identifying high performing and underperforming, identifying key customer, and to find out variation across providers

## Document Purpose ##
This documentation serves as a guide for project stakeholders, providing insights into the project's objectives, data sources, data analysis, visualizations, and any other relevant information.

## Use Case ##
This project for stock market data for current S&P 500 companies will provide valuable insights and improvements across various operational aspects. Different stakeholders and decision making personnel within the organization could leverage these findings to enhance their functionality. Here are key stakeholders who could make use of this analysis and benefit from it.

**Shareholders**  
- Use of Analysis: shareholders can leverage on this analysis when carrying out decision making guarding the companies and improve overall efficiency in day-to-day operations.
-	Benefits: this will help then to knowing the stock in the market to invest in
  
**Management team**
-	Use of Analysis: The management team can benefit from insightful analysis and know customer preferences, satisfaction levels, and overall market trends.
-	Benefits: More targeted marketing strategies, improved customer engagement, and increased sales.

 **Operational managers**
-	Use of Analysis: operational managers are able to plan and keep tracking of the day to day business trend and a better understanding of customer preferences and issues.
- Benefits: Enhanced customer satisfaction, increased sales, and improved customer retention

 ## Skills Demostrated ##
 
-	Data Connection in Power BI
-	Data Profiling
-	Data Cleaning and Transformation in Power Query
-	Data Analysis
-	Data Visualization
  
  **Data Source**
  
The project utilizes a dataset containing information on stock market from some companies. The dataset used for this analysis was downloaded from [Maven Analytics](https://mavenanalytics.io/data-playground?page=10&pageSize=5) website where datasets are available for project purpose. The dataset is a CSV file and it consist single tables with seven column which are symbol, date, open, high, low, close and volume. The row’s in the table contains about 497473 which is use in the data analysis, this data is from the period of 2014 and 2017

**Data Connection Details**

in Power BI, connecting to a CSV file involves specifying the location of the CSV file and defining the data import settings. Here are the steps taken in data connection in Power BI. 

![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/GET%20FILE%20PAGE.png)

![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/GET%20FILE%202.png)

![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/LAUNCH%20LOAD%20AND%20TRANSFORM%20WINDOWS.png)

## Data Profiling ##

Data profiling in Power BI helps to examining and analysing the characteristics and quality of data to gain insights into its structure, patterns, potential issues, and identify outliers. It helps to make informed decision on data cleaning and transformation. Power BI provides several tools and features that help to profile data effectively. These are column quality, column distribution and column profile.


## Data Cleaning and Processes ## 

Data cleaning in Power BI is a critical step in preparing your data for analysis. Here’s a rundown of how it can be done effectively using Power BI:

**Power Query Editor**
Power Query Editor is a powerful tool within Power BI for data cleaning and transformation. Here’s how you can use it:
•	Access Power Query Editor: Open Power BI Desktop and click on "Transform Data" to access Power Query Editor.
•	Remove Unnecessary Columns: Select columns you don’t need, right-click, and choose "Remove."
•	Filter Rows: Use filters to remove rows that don't meet certain criteria.
•	Replace Values: You can replace incorrect or missing values using the "Replace Values" option.
•	Handle Missing Data: Use options like "Remove Rows" (to remove rows with missing values) or "Fill Down" (to fill in missing values).
•	Change Data Types: Ensure each column has the correct data type (e.g., text, number, date) by selecting the column and using the data type drop-down.
•	Split and Merge Columns: Split columns based on delimiters or combine multiple columns into one.
•	Remove Duplicates: Use the "Remove Rows" > "Remove Duplicates" option to eliminate duplicate records.
•	Transform Data: Perform operations like transposing tables, pivoting/unpivoting data, or aggregating data.

-**For this project the following steps where carried out using DAX** ( Data Analysis Expressions), I Created The Following Column For Effective Data Manipulation And Analysis, Month No, Year, Day , Day Of The Week In Numbers, Volatility

   MONTH NO                                                 : FORMAT ([DATE], “mmmm”)
   YEAR                                                     : FORMAT ([YEAR], “YYYY”)
   DAY                                                      : FORMAT ([DATE], “ DDDD”)
   DAY OF THE WEEK IN NUMBERS                               : WEEKDAY ([DATE] )
   VOLATILITY                                               : [HIGH] – [LOW]

** THE FOLLOWING MEASURE WHERE CREATED USING THE FOLLOWING DAX expression **

•	AVG VOLUME BY DAY = AVERAGEX ( VALUE ( ‘DATA IN SQL S&P 500 Stock Prices 2013-2017’ [ day of the week]), [total sales])

•	Max volume date = calculate ( max ( ‘DATA IN SQL S&P 500 Stock Prices 2014-2017’ [date]), filter (‘DATA IN SQL S&P 500 Stock Prices 2014-2017’,[total sales] = maxx(All (‘DATA IN SQL S&P 500 Stock Prices 2013-2017’[date]), [total sales]))))

•	Top stocks volume = var maxdate [max volume date] return calculate (sum (‘S&P 500 Stock Prices 2014-2017’[volume]), filter (‘ SQL S&P 500 Stock Prices 2014-2017’, ‘ S&P 500 Stock Prices 2014-2017’ [date] = maxdate))

•	Total max sales = sum( ‘S&P 500 Stock Prices 2014-2017’[HIGH])

•	Total sales = sum( ‘S&P 500 Stock Prices 2014-2017’[VOLUME])

•	PERCENTAGE GAIN = CALCULATE ( [final closing balance]-[initial open bal]) * 100

•	Initial open bal = sum( ‘S&P 500 Stock Prices 2014-2017’[open])

•	Final closing bal = sum( ‘S&P 500 Stock Prices 2014-2017’[closing])

•	Max volatility       = max ([volatility])


The purpose of the above syntax from dax was to be able to answer the following question for correct data extrapolation and interpretations
•	Which date in the sample saw the largest overall trading volume? On that date, which two stocks were traded most?

•	On which day of the week does volume tend to be highest? Lowest?

•	On which date did Amazon (AMZN) see the most volatility, measured by the difference between the high and low price?

•	If you could go back in time and invest in one stock from 1/2/2014 - 12/29/2017, 

which would you choose? What % gain would you realize?                             

## Data Analysis and Insight ## 


![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/volume%20of%20two%20highest%20sales%20stock.PNG)

![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/vistual%202%20for%20two%20highest%20stock.PNG)

**The sample saw the largest overall trading volume and two stocks   were traded most**
-From the above stock evaluation using the line chart we can say January 2016 has the largest number of sales and the two stock will the highest volume was GE and MU STOCK for  the period under review. Where 76149513 and 44642115 stock was traded respectively 

![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/avg%20volume%20of%20daily%20stock%20sales%20by%20year.PNG)
![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/vistual%202%20avg%20daily%20sales.PNG)

From the result of the analysis carried out from the graphic relationship day 4 which happen to be Wednesday on the analysis saw the highest day to day volume, and day 2 was the lowest day this can be observe from the diagram below.

![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/stock%20volatilty%20by%20year.PNG)

--The most volatile period of the year was in 2016 where volatility ratio went to an all high 26.91 % displayed on the bar chart as pink, volatility means the period at which price variation happen in quick subsections.

![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/percentage%20gain%20by%20year.PNG)

--The highest percentage gain too place on and stock with greatest profit margin was 2016 with 0.5 million profit in quantity valuation. 

## The dashboard with complete visualisation of the analysis ## 

![](https://github.com/osarodion268/S-P-500-Stock-Prices/blob/main/complete%20dashboard%20of%20the%20project%202.png)

## Conclusion ##

•	The GE and MU STOCK were customer preferences 

•	How do we now increase the number of the stock in the market under this company’s name.

•	The management should take average of this by looking at the selling point of this two stock and implement same for other stock
 

