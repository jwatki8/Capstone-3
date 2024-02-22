# Capstone 3_Final_Report- Jessica Williams
# REACHING OUT TO OLD FRIENDS: A study of X-Wines and X-Wine customers
X-wines has been running into trouble retaining their customer base. The percentage rate for repeat customers is at the lowest it’s been in the last five years. The company is trying to generate ideas to keep current customers making more purchases. X wines would like to enhance their customer experiences by recommending wines to customers that they might be interested in. They are looking to build a recommender system based on the properties of their wine and the customer ratings.

## 1. Data
To investigate this question we I will use an X-wines dataset consisting of the following two dataframes:
•	XWines_Full_100K_wines (csv)-This file contains a list of 100,000 wines and some of their attributes. The attributes include Type, Elaborate, Grapes, Harmonize, ABV, Body, Acidity, Region, Winery and Vintages.
•	XWines_Full_21M_ratings(csv file)- This file contains a set of 21 million user ratings of wines on a scale of 1-5.

## 2. Data Wrangling

[Full Data Cleaning Report](https://github.com/jwatki8/Capstone-3/blob/main/Capstone%203%20Data%20Wrangling.ipynb)

This was a fairly clean dataset so most of my data wrangling time was spent examining the column values. Here are a few of the steps that I took:
- Dropped the website column from the wine list dataframe as I know that won’t be useful for my analysis.
- Examined the value counts of most of the attribute columns in the wine list dataframe to view the available responses for each variable.
- Checked the wine list dataframe for null values and found none.
- Made sure no specific wine ID was repeated in the wine list dataframe. 
- Found out the value range for the ratings in the wine ratings dataframe is1-5.
- Counted the number of unique raters in the wine ratings dataframe.
- Examined the frequency of the different individual raters.
- Created a mean rating column for the wine ratings dataframe that represented the mean of the ratings given for each unique wine.

## 3. EDA

[Full EDA Report](https://github.com/jwatki8/Capstone-3/blob/main/Capstone%203-Exploratory%20Data%20Analysis%20(EDA)%20Draft.ipynb)

### Creating more features
To aid in more effective analysis, I added a few extra variable columns to the data. In order to take a look at how many times our raters rated different wines, I added a column called rater count. This column summed the number of rating rows for each unique rater. The rater count column displayed a range of 5 to 2986 and confirmed that multiple ratings were available for all of our users.

I also added a column for the mean rating of each rater. From this column I was able to see that the higher frequency raters have lower rating means as would be expected with having more data to summarize over.  

Since the dataset contained a lot of categorical variables, I decided to create dummy variables for a few of the categories that seemed most useful. I created dummy variables for the ‘Type’, ‘Elaborate’, ‘Body’, and ‘Acidity’ Columns.

### Merging effectively
Since the dataset existed in two different dataframes(wine_list and wine_ratings) I needed to merge the two dataframes to combine the information. I mergered the wine_list dataframe to the wine_ratings dataframe on the WineID column. The columns I pulled from the wine _list dataframe were the 'WineID', 'WineName', 'Type', 'Elaborate', 'Grapes', 'Harmonize', 'ABV', 'Body', 'Acidity', 'Country', 'RegionID', 'RegionName', 'WineryID', 'WineryName', and the 'Vintages' columns. To make this a simpler process I merged the dataframes before adding the dummy variables to the final dataframe.

### Distributions

First I examined the distribution of the ratings. 

![Screenshot of Rating Distribution.](/Read%20me%20files/rating%20percent%20dist.png)

From this plot I noticed a few things
- 4.0 is the most frequent rating with 40% of the distribution.
- Most of the ratings for the wines are above 3.0.
- the users can give .5 ratings as a part of the value ranges (ex. 1.5, 2.5)
- there is a significant count for all of the possible ratings.
I also took a look at the rating distribution for some of the wine attribute variables starting with the ‘Acidity’ variable. 

![Screenshot of correlation map.](/Read%20me%20files/Acidity%20dist.png)

![Screenshot of correlation map.](/Read%20me%20files/acidity%20dist%202.png)

‘High’ acidity wines seemed to have a large representation in all of the rating values but it also accounted for 80% of the wine distribution. A similar pattern emerged with the distribution of the ‘Body’ variable. ‘Full bodied’ wines had the largest representation on the high ratings but this category accounted for almost 50% of the wine distribution.

Since looking at this information over our entire dataset wasn’t quite as useful as I would like it to be, I tried to examining the wines with the highest average rating. I started with a subset of rating means above 4.8. Within this subset the distribution for the ‘Acidity’ attribute remained the same. However, the distribution for the ‘Body’ variable did change. 

![Screenshot of correlation map.](/Read%20me%20files/Body%20dist.png)

![Screenshot of correlation map.](/Read%20me%20files/Body%20ratings%20dist.png)


