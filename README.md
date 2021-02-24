# Kickstarting with Excel
## Overview of Project
### Purpose
Fundraising is one of the most important steps to make a play to be performed on big stage. There are
different factors that will affect the successfulness of the fundraising campaign. For example, based
on different country and time period, the goal of fundraising might be affected by the timeline. A
thorough data analysis will help the owner to have a reasonable expectation and make decision on the 
fundraising campaign.

As Louise’s play Fever came close to its fundraising goal soon, we are going to analyze the Kickstarter
data to help Louise better understand the relationship between launch date or funding goals and the
fundraising campaign outcomes. This analysis will help Louise to gather additional information to
success fundraising campaign. 

## Analysis and Challenges
### Analysis of Outcomes Based on Launch Date
1.	The launch date in the original Kickstarter dataset was in UNIX timestamp format. Used the following function to convert it to a readable format:

![Screenshot](screenshot1.png)
    
 where J* indicates each cell in column J (launched_at).
 
2.	Used YEAR() function to get the year the converted launch dates.
3.	Created pivot table “Theater Outcomes Based on Launch Date”, which has "Parent Category" and "Year" as the filters, the months of launch date as the rows, and outcomes as the columns. There are four outcomes: “successful”, ”failed”, “canceled” and “live”. Filtered the outcomes to hide the outcome “live”. In addition, filtered the "Parent Category" to "theater".
4.	Sorted the data by the number of outcomes in descending order for each month to made outcome “successful” to be the first column.
Final PIVOT Table:
 
5.	Based on the pivot table created from step4, created a line chart which has the month of launch date as X-axis and the number of outcomes in Y-axis.
6.	In the initial line chart that created based on the pivot table, the filters were included in the chart. Right click the filters, and select "Hide Report Filter Buttons on Chart" to hide the filters.
Final Line Chart:


 
### Analysis of Outcomes Based on Goals
1.	Created a table frame in a new sheet that has 8 columns. The first column “Goal” contains 12 categories. The other 7 columns will be calculated based on the criteria of each categories in the first “Goal” column.
2.	Based on the number range in each category in the “Goal” column, filtered the Kickstarter data to  “Subcategory” equals to “plays”, then use the value from the “goal” column in the Kickstarter sheet to count the number of successful, failed and canceled in column B, C and D respectively. Used COUNTIFS() function to calculate the numbers.
Example:

 
Where F indicates column F in the Kickstarter data sheet (outcomes).

D indicates column D in the Kickstarter data sheet (goal).

S indicates column S in the Kickstarter data sheet (Subcategory).


3.	Summed the number of outcomes calculated in column B, C and D as "Total Projects" in column E.
Ex:  

4.	Used the number of outcomes in column B, C and D, and the "Total Projects" in column E to calculate the percentage for successful, failed and canceled in column F, G and H respectively.
Ex:  
Final table:
 
5.	Based on the final table created in step4, created a line chart, with each categories of the Goal column as X-axis, percentage of outcomes as the Y-axis.
 
### Challenges and Difficulties Encountered
1.	The UNIX time stamp format of the launch date stored the seconds instead of actual date. Need to use function to convert it to readable date value. The function will convert the seconds to days and adding the date value for January 1st, 1970, which is the “Unix Epoch”.
2.	In the Analysis of Outcomes Based on Goals, the calculate 

## Results
- What are two conclusions you can draw about the Outcomes based on Launch Date?
1.	Regardless of the year and country, May has the largest number of successful. This might because in most of the countries in the Kickstarter data, it is starting to get warm in the middle of the year, and people will be more interested in get out
2.	Regardless of the year and country, in December there were similar number of successful and failed. This might because December is considered as in the holiday season, less people interested in going to theater. 
- What can you conclude about the Outcomes based on Goals?
1.	There is no canceled campaign for subcategory “plays”.
2.	For each categories of the Goal, the percentage of successful and failed sum up as 100%. In category “Less Than 1,000” to “25,000 to 29,000” the percentage of successful decreased, while the percentage of failed increased. Category “45,000 to 49,000” has the highest percentage of successful and the lowest percentage of failed. Although the percentage of failed decreased between “25,000 to 29,000” and 35,000 to 39,000”, the overall trend showed us that the higher the number of goals set up for the fundraising campaign, the higher possibility of failed.  
- What are some limitations of this dataset?
1.	In the Kickstarter data sheet, the values in the goal and pledged columns are in different currency. There is no standardized amount of month for both. When checking the outcomes based on the goal column, the output will be biased by the difference among each currency. 
2.	There is no information of actual strategy for each fundraising campaign. For example, the fundraising campaign was hold through social media, or use printed poster to be shown in public, or used combine strategies. The different strategy used throughout the fundraising campaign will affect the outcomes. 
- What are some other possible tables and/or graphs that we could create?

