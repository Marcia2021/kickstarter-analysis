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
 
2.	Used YEAR() function to get the year from the converted launch dates in Step1.
3.	Created PIVOT table “Theater Outcomes Based on Launch Date”, which has "Parent Category" and "Year" as the filters, the months of launch date as the rows, and outcomes as the columns. There are four outcomes: “successful”, ”failed”, “canceled” and “live”. Filtered the outcomes to hide the outcome “live”. In addition, filtered the "Parent Category" to "theater".
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
    ![screenshot8](https://user-images.githubusercontent.com/79289806/108928781-c022ea00-7610-11eb-9db4-b032cf79a338.png)
 
5.	Based on the final table created in step4, created a line chart, with each categories of the Goal column as the X-axis, the percentage of outcomes as the Y-axis.

    ![screenshot9](https://user-images.githubusercontent.com/79289806/108928782-c022ea00-7610-11eb-8f9a-befe5fea909e.png)

 
### Challenges and Difficulties Encountered
1.	The UNIX time stamp format of the launch date stored the seconds instead of actual date. Need to use function to convert it to readable date value. The function will convert the seconds to days and adding the date value for January 1st, 1970, which is the “Unix Epoch”. 
2.	In the Analysis of Outcomes Based on Goals, the PIVOT table will be used to create a line chart. When calculate the percentage, I multiplied the value by 100 and round to 2 decimal places. In this way, when creating the line chart, the Y-axis will not be able to show up as percent with % at then end. I kept the raw value from the percentage calculation, then use "percentage" as the data format for the Y-axis to present as actual percent value.

## Results
- What are two conclusions you can draw about the Outcomes based on Launch Date?
1.	Regardless of the year and country, May has the largest number of successful. This might because in most of the countries in the Kickstarter data, it is starting to get warm in the middle of the year, and people will be more interested in out-of-house activity. Watch a show or play might be one of the popular family friendly activity based on the Kickstarter data’s target population.
2.	Regardless of the year and country, in December there were similar number of successful and failed. This might because December is considered as in the holiday season, less people are interested in going to theater. 
- What can you conclude about the Outcomes based on Goals?
1.	There is no canceled outcomes for subcategory “plays” in the Kickstarter data.
2.	For each categories of the Goal, the percentage of successful and failed sum up as 100%. Among the categories “Less Than 1,000” and “25,000 to 29,000” the percentage of successful decreased, while the percentage of failed increased. Category “45,000 to 49,000” has the highest percentage of successful and the lowest percentage of failed. Although the percentage of failed decreased between “25,000 to 29,000” and 35,000 to 39,000”, the overall trend showed us that the higher the number of goals set up for the fundraising campaign, the higher possibility of failed.
3.	Although this particular analysis only focused on the relationship between goal and outcomes for “plays”, the line chart showed that their will be other factors that affect the outcomes along with the goal. For example, the type of the “plays”, or the actual location of the “plays” that planned to be shown might be one of the initial factors that decide the amount of money for the goal. This might explain the trend changes in the line chart. 
- What are some limitations of this dataset?
  
  There are lots of factors that will affect the reliability of the data, which will further affect the analysis outputs. Depending on the different analysis     purpose, we might focus on different feather of the data. Here are some general limitations of the Kickstarter data.
1.	In the Kickstarter data sheet, the values in the goal and pledged columns are in different currency. There is no standardized amount of month for both. When checking the outcomes based on the goal column, the output will be biased by the differences among each currency. 
2.	There is no information of the actual strategy for each fundraising campaign. For example, the fundraising campaign was hold through social media, or used printed poster to be shown in public, or used combine strategies. The different strategy used throughout the fundraising campaign will affect the outcomes. 
3.	The demographic information of the target population in the Kickstarter data is unclear. Age group, gender, race and other demographic information will also affect the outcomes of the fundraising campaign.  

- What are some other possible tables and/or graphs that we could create?

