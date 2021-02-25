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
success in fundraising campaign. 

## Analysis and Challenges
### Analysis of Outcomes Based on Launch Date
The first analysis is to looking at the relationship between the launch date and the outcomes of the fundraising campaign. 
1.	The launch date in the original Kickstarter dataset was in UNIX timestamp format. Used the following function to convert it to a readable format:

    ![screenshot1](https://user-images.githubusercontent.com/79289806/108928628-79cd8b00-7610-11eb-8b3e-49d0845ddd6c.png)
    
    where J* indicates each cell in column J (launched_at) in the Kickstarter data sheet.
 
2.	Used YEAR() function to get the years from the converted launch dates in Step1.
3.	Created PIVOT table “Theater Outcomes Based on Launch Date”, which has "Parent Category" and "Years" as the filters, the months of launch date as the rows, and outcomes as the columns. There are four outcomes: “successful”, ”failed”, “canceled” and “live”. Filtered the outcomes to hide the outcome “live”. In addition, filtered the "Parent Category" to "theater".
4.	Sorted the data by the number of outcomes in descending order for each month to made outcome “successful” to be the first column.

    Final PIVOT Table:

    ![screenshot2](https://user-images.githubusercontent.com/79289806/108938802-b6a07e80-761e-11eb-81af-828c526246df.png)
 
5.	Based on the PIVOT table created from step4, created a line chart which has the month of launch date as the X-axis and the number of outcomes as the Y-axis.
6.	In the initial line chart that created based on the PIVOT table, the filters were included in the chart. Right click the filters, and select "Hide Report Filter Buttons on Chart" to hide the filters.

    Final Line Chart:

    ![screenshot3](https://user-images.githubusercontent.com/79289806/108928785-c0bb8080-7610-11eb-9f99-faf4424fc9f5.png)

 
### Analysis of Outcomes Based on Goals
This analysis is looking at the relationship between the goals for the fundraising campaign and the outcomes.
1.	Created a table frame in a new sheet that has 8 columns. The first column “Goal” contains 12 categories. The other 7 columns will be calculated based on the criteria of each categories in the “Goal” column.
2.	Based on the number range in each category in the “Goal” column, filtered the Kickstarter data to  “Subcategory” equals to “plays”, then use the value from the “goal” column in the Kickstarter sheet to count the number of successful, failed and canceled in column B, C and D respectively. Used COUNTIFS() function to calculate the numbers.
	
    Example:
    
    ![screenshot4](https://user-images.githubusercontent.com/79289806/108928777-c022ea00-7610-11eb-84b3-98580a0ed9a9.png)
    ![screenshot5](https://user-images.githubusercontent.com/79289806/108928778-c022ea00-7610-11eb-90c6-6af2ed553128.png)
 
    Where F indicates column F in the Kickstarter data sheet (outcomes).

    D indicates column D in the Kickstarter data sheet (goal).

    S indicates column S in the Kickstarter data sheet (Subcategory).

3.	Summed the number of outcomes calculated in column B, C and D as "Total Projects" in column E.

    Ex:  ![screenshot6](https://user-images.githubusercontent.com/79289806/108928779-c022ea00-7610-11eb-8b25-892715417db9.png)

4.	Used the number of outcomes in column B, C and D, and the "Total Projects" in column E to calculate the percentage for successful, failed and canceled in column F, G and H respectively.

    Ex:  ![screenshot7](https://user-images.githubusercontent.com/79289806/108928780-c022ea00-7610-11eb-9075-b00f36e64a74.png)
    
    Final table:
   ![screenshot8](https://user-images.githubusercontent.com/79289806/109091116-30e60700-76e2-11eb-85d2-196e29bfd905.png)
 
5.	Based on the final table created in step4, created a line chart, with each categories of the Goal column as the X-axis, the percentage of outcomes as the Y-axis.

    ![screenshot9](https://user-images.githubusercontent.com/79289806/108928782-c022ea00-7610-11eb-8f9a-befe5fea909e.png)

 
### Challenges and Difficulties Encountered
1.	The UNIX time stamp format of the launch date stored the seconds instead of actual date. Need to use function to convert it to readable date value. The function will convert the seconds to days and adding the date value for January 1st, 1970, which is the “Unix Epoch”. 
2.	In the Analysis of Outcomes Based on Goals, the PIVOT table will be used to create a line chart. When calculate the percentage, I multiplied the value by 100 and round to 2 decimal places. In this way, when creating the line chart, the Y-axis will not be able to show up as percent with % at then end. I kept the raw value from the percentage calculation, then use "percentage" as the data format for the Y-axis to present as actual percent value.

## Results
- What are two conclusions you can draw about the Outcomes based on Launch Date?
1.	Regardless of the year and country, May and June have the largest number of successful. When conducting fundraising campaign, these two months will have a higher possibility of success. This might because in most of the countries in the Kickstarter data, it is starting to get warm in the middle of the year, and people will be more interested in out-of-house activity. Watch a show or play might be one of the most popular family friendly activity based on the Kickstarter data’s target population.
2.	Regardless of the year and country, the number of total fundraising campaigns decreased after June. December has the smallest number of successful compared to the other months. Additionally, the number of successful and failed are very close to each other in this month. Towards the end of the year, there are less fundraising campaign projects and has lower rate of successful, as this might related to other factors that didn’t included in this analysis. 
- What can you conclude about the Outcomes based on Goals?
1.	There are no canceled outcomes for subcategory “plays” in the Kickstarter data. This means among all the fundraising campaigns for “plays”, no matter it is successful or failed, all the campaigns were able to proceed as planned. 
2.	The category "1,000 to 4,999" has the largest number of fundraising campaigns for "plays" across all the categories. In this category, the rate of successful is much higher than the rate of failed. This means among all the fundraising campaigns for “plays”, majority of the campaigns set the goal between 1,000 and 4,999 which leads to a higher possibility of success. This might depend on the size of the show and other factors which were not included in the Kickstarter data and this analysis.
3.	Although this particular analysis only focused on the relationship between goal and outcomes for “plays”, the distribution of the number of outcomes and percentage in the line chart showed that there will be other factors that affect the outcomes along with the goal. For example, the type of the “plays”, or the actual location of the “plays” that planned to be shown might be one of the initial factors that decide the amount of money for the goal. This might explain the trend changes in the line chart. 
- What are some limitations of this dataset?
There are lots of factors that will affect the reliability of the data, which will further affect the analysis outputs. Depending on the different analysis purposes, we might focus on different feature of the data. Here are some general limitations of the Kickstarter data.
1.	In the Kickstarter data sheet, the values in the goal and pledged columns are in different currency. There is no standardized amount of money for both. When checking the outcomes based on the goal column, the output will be biased by the differences among each currency. 
2.	There is no information of the actual strategy for each fundraising campaign. For example, the fundraising campaign could be hold through social media, or used printed poster to be shown in public, or used combined strategies. The different strategy that has been used throughout the fundraising campaign will affect the outcomes. 
3.	The demographic information of the target population in the Kickstarter data is unclear. Age group, gender, race and other demographic information will also affect the outcomes of the fundraising campaign.  
- What are some other possible tables and/or graphs that we could create?
Depending on the purpose of different analysis, there are few tables we could create.
1.	Check the relationship between the fundraising timeline and outcomes. Here are the general steps:
Convert the deadline in the Kickstarter data to a readable date value by using the same function as we used for converting the launch date. Then calculate the difference between the deadline line and launch date. This difference will be calculated in days. We could create a new table frame with Timeline in the first column which has 7 categories based on the difference of the days between deadline and launch date. Then count the number and percentage of the outcomes for “plays”.
Table:

![screenshot10](https://user-images.githubusercontent.com/79289806/109088049-a64ed900-76dc-11eb-9966-ebd90e4ef125.png)
 
We can use this table to create two separate line charts for percentage and number of outcomes by timelines respectively:
 

![screenshot11](https://user-images.githubusercontent.com/79289806/109088074-b5358b80-76dc-11eb-90b7-154c82afe4b9.png)
![screenshot12](https://user-images.githubusercontent.com/79289806/109088081-b8307c00-76dc-11eb-855e-1c529aec5ed6.png)
 
From the table and chart above, we could see that one to one and half month of the fundraising campaign timeline could lead to higher possibility of successful. 
2.	Check the relationship between parent category and goal by outcomes. Here are the general steps:
In the Kickstarter data, created a category variable “Category of Goal” based on the value of goal column. I created four categories (shown in the table below). Then created a PIVOT table, used country and outcomes as the filters, parent category as the rows, Category of Goal as the columns, and number of outcomes as the values.
PIVOT Table:

![screenshot13](https://user-images.githubusercontent.com/79289806/109088147-dc8c5880-76dc-11eb-9674-309b9d148159.png)
 
We could filter the country and outcomes to better understand the relationship between each category of the fundraising campaign and the goals that will lead to different outcomes. 


