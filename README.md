# Kickstarting with Excel

## Overview of Project

### Purpose
Louise is an aspiring playwrite itching to break into the theater industry, however, if she's going to do it, she's going to do it right!  Louise initially reached out priror to launching a Kickstarter campaign to raise money for her play, "Fever," looking to understand trends between successful, failed, and canceled campaigns within the industry.  After launching a campaign and coming close to her funding goal, Louise asked if we could circle back to the dataset to see how other campaigns fared in relation to their launch date and funding goal.  For this analysis, we created pivot tables and charts that clearly visulized the realtions between campaign ourcomes and these two factors.    

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
To analyze the realtionship between a campaign's outcome and launch date, we started by creating a pivot table that showed Louise a count of successful, failed, and canceled campaigns for each month with the ability to filter by year and parent category.  To do this, we needed one more piece of data, so, followed the steps below:


-  Parse the year from the Date Created Conversion column and create a new column for this data point alone using the Excel function, Year().  We will need this information so that Louise can filter her table by year if she pleases.  
---
After obtaining this last piece of information, we were ready to create our pivot table.  We made the table to see an exact count of successful, failed, and canceled campaigns for each month by setting the months (Date Created Conversion) as the row lables, Outcomes as columns, and Count of Outcomes as our values.  Additionally, we added Year and Parent Category filters to help Louise narrow down the data as much as she wanted.

---
From here, we wanted to help Louise answer the question, "What are the best months to launch a campaign?" at a glance by creating a line chart.  We generated this by using the pivot table, putting months on the x-axis and count of outcomes on the y-axis.  

![Theater_Outcomes_vs_Launch_Date](https://user-images.githubusercontent.com/94569240/146788680-84d1350b-3513-4aac-a90f-d1959c5eae33.png)
---
#### Challenges Faced in this Analysis 
1. When creating the pivot table and adding Date Created Conversion to the row fields, other, unnecessary (for this analysis' requirments), fields populated along with it; so the table did not instantly show the months as the row lables like Louise wanted.  To overcome this, I played around with the additional row fields and deleted what I beleived to be unnecessary until only the months showed in the table!  
2. In the pivot table fields guide, the values always default to "Sum of **X**" which is not the information we wanted to display.  Thus, a quick adjustment to "**Count** of X" allowed us to see the total number of successful, failed, and canceled campaigns as Louise requested.  
---
### Analysis of Outcomes Based on Goals
Louise also asked us to look into the relationship between a campaign's outcome and its funding goal.  For this, we set out to create another pivot table and chart to summarie the percetage of successful, failed, and canceled campaigns based on what thier fundraising goal was. 

---
We couldn't use each indivisual fundraising goal as a datapoint for this, so we established "Goal Ranges" to categorie each campaign.  Starting with goals of less than $1,000, we created 12 categories that increased by $5,000 at a time.  Our final list looked like:

---
- Less than 1000
- 1000 to 4999
- 5000 to 9999
- 10000 to 14999
---
... and so on until we got to $49,999, when we ended our list with campaign goals greater than or equal to $50,000.

---
From here, we used the COUNTIFS() function to count the number of successful, failed, and canceled campigns for plays within each goal range.  Each equation looked different based on the critera we were asking Excel to search for, but an example of one is below:

---
- "=COUNTIFS('Kickstarter Data'!D:D, ">=1000", 'Kickstarter Data'!F:F, "successful", 'Kickstarter Data'!P:P, "plays", 'Kickstarter Data'!D:D, "<=4999")"
---
After obtaining the final count of each play campaign's outcome, it was time to find a total for each fundraising goal range using the "=SUM()" function.  

---
Having this sum allowed us to then calculate what we really needed: the percentage of of successful, failed, and canceled campigns in each fundraising goal range.  We did this by just dividing the specific counts by the total project sum.  Then we were left with a sheet that looked like this:

---
Then, we were ready to make our pivot line chart!

---
We started with a pivot table that reiterated the information on the Outcomes Bassed on Goals sheet which helped us easily create the pivot chart with the same information.  

---
With our Goal in the X-Axis, percentage Values in the columns, and Product of Percetages for each outcome in the values position, out pivot line chart was complete.  With this artifact, Louise could now see the relationship between an outcome and a fundraising goal at a glance!

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/94569240/146789434-0a13593c-0590-4f29-8083-e6c85e4631d5.png)

---
#### Challenges Faced in this Analysis
This analysis was challenging in many ways!  
1. This was my first time using the COUNTIFS function so it took multiple tutorials for me to digest how the funtion was organized to communicate with Excel.  Eventually, I understood the formatting as:
  - "=COUNTIFS(look in this column, "for this criteria", then look in this column, "for this  criteria") and so on.  
After I got the hang of it, using this funtion felt like second nature!
2. After clearing my first hurdle, I then ran into a roadblock when formatting the pivot chart.  For some reason, the pivot table wasn't sorting the Goal values in the order I had placed them in so the chart wasn't telling a coherent story of the increasing data. 
     for example, the list looked like this:
   - 1000 to 4999
   - 10000 to 14999  
   - 5000 to 9999
   - Less than 1000
I overcame this by utilizing the "More Sort Options" button on the filtering page and selected the option to manually rearrange the fields how I wished.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
  1. May, June, and July are the best months to launch a campaign.  If you can, try to launch your campaign in May as it has the highest success rate of the three with 66% of the 166 campaigns succeeding.
  2. No matter what time of year a campaign is launched, more campaigns are successful rather than failures by about 26%.
     - This was found by calculated the percentages of successes, failures, and canceled theater campaigns, finding the median of sucesses (61%) and failures (35%), and taking the difference of the two medians to get a 26% difference in an additional sheet I did not inlcude in the final document.  
---
- What can you conclude about the Outcomes based on Goals?
  1. Campaigns with goals less than or equal to $5,000 saw the highest sucess rates with an average of 74% of the projects succeeding in their fundraising.  this seems to be the fundraising sweetspot and I'd reccomend Louise staw within this range if possible.  
---
- What are some limitations of this dataset?
  1. One limitation is that we do not have insight into how many of the campaign hosts, like Louise, are first time playwrites with no pre-exisiting relationships with potential backers.  Hosts having wirtten plays and running fundraising campigns previously could create a bias for backers to be more likely to contribute to that platwrite more than others. 
     - This dataset could have included a column for "First Time Campaigners" with Yes or No as values to give us better insight into the fundraising "playing field". 
  2. Becasue we were not the ones to pull this dataset, we cannot totally trust that this dataset is accurate.
  ---     
- What are some other possible tables and/or graphs that we could create?
  1. A table, just like the one we created for Outcomes Based on Goals, that measures the percentages of success, failure, and cancelations for Theater Outcomes by launch date to help Louise understand her chances of launching a campaign in one month versus another.  
  2. It may also be helpful to create a table that measures the success rate of campaigns based on what their fundraising goal was and how long their campaign ran for. 

