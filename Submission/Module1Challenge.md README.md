# **Kickstarting with Excel**

## *Overview of Project*

### Purpose: The purpose of this project was to both create new data by executing Excel functions on existing data in the Kickstarter data sheet for Module 1 (including some newly formed column data based off of the asynchronous work), and then taking that newly created data and presenting it visually so that Louise can get a better picture of how different Kickstarter campaigns for plays fared depending on their launch date and funding goals. 

## *Analysis and Challenges*

### Analysis of Outcomes Based on Launch Date

In this analysis, a pivot table was created based off of a few columns of data in the Kickstarter worksheet. First, all of the data was selected, and Insert -> Pivot Table was utilized. Then, the data was filtered by the parent category and years, with "theater" being specified as the parent category. 

I put the "outcomes" column in the columns of the pivot table and then filtered out the results for "live" outcomes, then filtered the column labels in descending order so that only successful, failed, and canceled outcomes in that order would appear. The "outcomes" column was again placed in the "values" part of the pivot table, so that the amount of Kickstarters, sorted by month, could be assessed with the "Date Created Conversion" column being placed for rows. 

The grouping function had to be utilized here, as putting the newly created "Years" or "Date Created Conversion" columns in the rows of the pivot table did not sort by month. I right clicked the row labels and sorted by months ONLY so that the best time of year to launch a Kickstarter for a play, sorted by month, could potentially be deduced from the data. 

This analysis was represented by the chart depicted in Theater_Outcomes_vs_Launch.png. 

https://github.com/DAKupratis/kickstarter-analysis/blob/main/Submission/resources/Theater_Outcomes_vs_Launch.png

The data sheet can also be observed by the screenshot at the link below.

https://github.com/DAKupratis/kickstarter-analysis/blob/main/Submission/resources/outcomesLaunchDataSheet.png

### Analysis of Outcomes Based on Goals

The chart depicted in Outcomes_vs_Goals.png zeroes in more specifically on the success rate of "Plays", a subcategory of the parent category "Theaters" depicted  in the prior sheet's analysis, sorted by fundraising goal amounts. The chart can be found at the link below.

https://github.com/DAKupratis/kickstarter-analysis/blob/main/Submission/resources/Outcomes_vs_Goals.png


In order to create this analysis, a new sheet was created, titled "Outcomes Based on Goals". In this sheet, the =COUNTIFS function was utilized to count the totals of Kickstarter campaigns of the "plays" subcategory, depicted on the primary data sheet that met their funding goals, failed to meet their funding goals, and those that had to cancel their fundraisers. The outcomes were sorted by funding goals at less than $1,000, and then at $5,000 intervals from $4,999 to $49,999, followed by all results above $50,000.

Two examples of this formula include...

a) Counting successful "plays" kickstarters with fundraising goals <$1,000.

=COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,"<1000", Kickstarter!$R:$R, "plays")

...where the first criteria and range provides the worksheet and outcome column in which it is contained to search for, the second criteria and range provides the worksheet and goal column in which to tie the first criteria and range to, and the final criteria and range provides the worksheet and subcategory of Kickstarter campaign to tie to the first two with. If values are found for all three, the total is summed up. Note that since we are only counting everything beneath $1,000, there are less criteria and range to write into this formula (3) than it would be if we were counting all true values between two goal ranges (4). This same formula applies to Kickstarters above $50,000, as there is no additional boundary to create the same way there is no lower boundary to create for Kickstarters <$1,000. 


b) Counting failed "plays" kickstarters with fundraising goals between $10,000 and $14,999.

=COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,">=10000", Kickstarter!$D:$D,"<=14999", Kickstarter!$R:$R, "plays")

...where two goal ranges as mentioned above are counted for. All functions are repeated, save for an additional criteria and range that creates a boundary for which the function should search for data. In this example, we add "Kickstarter!$D:$D,"<=14999" to capture all true values within the specified range. Thus, there are four criteria and range. 

Then, we counted the success/failure/canceled rate percentages for each goal category by taking the total, dividing the "part" ("success/failure/canceled") by the whole ("total projects") and multiplying by 100 to arrive at a total number percentage. 

An example formula is that for percentage failed for Kickstarters between $5,000 and $9,999. See below.


=(C4/E4)*100

...where C4 = the amount failed at the goal range, E4 = the total amount of subcategory projects at the goal range, and *100 brings it to a number to be reported as a percent. 

Note that this was not formatted as a "percentage" cell, as that would have arrived at inaccurate values in the thousands of percents. 

The data sheet can be seen in the screenshot below.

https://github.com/DAKupratis/kickstarter-analysis/blob/main/Submission/resources/outcomesGoalsDataSheet.png

### Challenges and Difficulties Encountered

I encountered two primary challenges during this assessment, one for each deliverable. 

A) For the source data resulting in the Theater_Outcomes_vs_Launch.png 		deliverable, I realized that the newly created "Years" column, when utilized to assess outcomes by month by placing it in the "rows" part of the pivot table didn't provide me an option to filter by month. Thus, I placed the "Date Created Conversion" column data in the rows of the pivot table, as that contained month data. Then, I had to utilize the Grouping function for Pivot Tables as described in the following link: https://support.microsoft.com/en-us/office/group-or-ungroup-data-in-a-pivottable-c9d1ddd0-6580-47d1-82bc-c84a5a340725?ui=en-us&rs=en-us&ad=us so that the data would be laid out by month. 

From here, I was able to successfully sort by month, with totals, to match the example provided in the challenge. This grouping function can be seen in the screenshot linked below.

https://github.com/DAKupratis/kickstarter-analysis/blob/main/Submission/resources/groupingDates.png

B) I was having a hard time replicating the formula while retaining the same reference cells for each column when clicking the bottom right corner of the cell. I had not realized that in order to retain the same reference cells when carrying a formula forward, the row and column ranges had to be precluded by a "$" each.

So, instead of...

=COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,"<1000", Kickstarter!$R:$R, "plays")

The above formula was shifting over a column when trying to click the bottom right corner of the cell without the "$" values precluding each row and cell range. Once realizing this, I was able to edit the formulas and obtain the desired result. 

As an aside, there was a touch of confusion when the number canceled was 0 across the board. I was able to verify that this was not an error by simply filtering the primary data sheet to match the categories in the =COUNTIFS function, and saw that there were indeed 0 canceled.


## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

As visualized in Theater_Outcomes_vs_Launch.png, the order of which months of the year yield the highest number of successful Kickstarter launches for Theater productions is as follows...

**Most successes per month, ranked**

1) May: 111
2) Jun: 100
3) Jul: 87
4) Aug: 72
5/6) Feb/Apr: 71
7) Oct: 65
8) Sep: 59
9/10) Jan/Mar:56
11) Nov: 54
12) Dec: 34

Two (oversimplified) conclusions one could draw about this data are...


1) That June specifically has the highest amount of successful launches and thus **might appear** to be the most optimal time to launch a Kickstarter campaign for a theater production. More generally, the run of months from late Spring to late Summer have the first through fourth highest amounts of successful Kickstarter campaigns for Theater productions. 

2) However, a month having the highest amount of successful kickstarters doesn't necessarily mean that less failed. For instance, May also had the highest number of failed campaigns at 52, and two more of the top four months for successful kickstarters, July and June, also make appearances for the greatest number of failed kickstarters in a tie for second place and a fourth place rankings respectively. A full ranking is below. 

**Most failures per month, ranked**


1) May: 52
2/3) Jul/Oct: 50
4) Jun: 49
5) Aug: 47
6) Apr: 40
7) Feb: 39
8) Dec: 35
9) Sep: 34
10/11) Jan/Mar: 33
12) Nov: 31

- What can you conclude about the Outcomes based on Goals?


Two (also oversimplified) conclusions one could draw about this data are...

In general, most successful Kickstarter campaigns for Plays occur at lower fundraising goals. The overall frequency of goals under $5,000 being met far surpasses all other goal categories, though this is not accurately represented by assessing success rates. Though Outcomes_vs_Goals.png does depict the highest success rates as generally being found found at fundraising goals set at less than $5,000 (<$1,000 = 75.81% and $1,000 to $4,999 = 72.66%), both categories of goals between $35,000 and $44,999 are not far behind at 66.67% success rates each. That said, there are only 9 campaigns in total being assessed with goals between $35,000 and $44,999, whereas there are 720 campaigns being assessed with goals set under $5,000. 

- What are some limitations of this dataset?

1. A limitation of the dataset when sorting Theater Outcomes by Launch Date is that assessing the odds of success by the only considering the total count of successful/failed/canceled plays Kickstarters per month makes the likelihood of success appear far more dramatic than a line chart depicting totals would present. If you assess the chart by percentages, as seen by the screenshot looked below, the difference between high success count months appears far less dramatic. It would thus appear that more succeeded primarily because more were attempted in the first place. Which month a campaign is launched might not have as significant as a correlation with success accordingly. 


2. A limitation of the dataset when sorting outcomes based on goals is that sorting the data by success rate alone wouldn't capture that there is a considerably larger amount of data for Kickstarter campaigns with lower fundraising goals. It is hard to draw concrete conclusions about Kickstarter campaigns for plays as the fundraising goal gets higher. For instance, there are less than twenty total campaigns to analyze by fundraising goal above $20,000. It is right skewed data which is not an adequate sample size.

3: All of this infers that correlation = causation. Many factors beyond just the date at which a Kickstarter is launched may affect the analysis.  


- What are some other possible tables and/or graphs that we could create?

Limitation 1 is observed by assessing success rates of each outcome, sorted by goal, in the chart below. 

https://github.com/DAKupratis/kickstarter-analysis/blob/main/Submission/resources/outcomePercentagesByLaunchDate.png

Limitation 2 is observed by counting each data subset per fundraising goal category, in the chart below.

https://github.com/DAKupratis/kickstarter-analysis/blob/main/Submission/resources/projectsCountByGoal.png
