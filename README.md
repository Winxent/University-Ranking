# University-Ranking
Goal: Data analysis using google collaboratory python pandas on university ranking dataset

![rainbow](https://github.com/Winxent/portfolio/assets/146320825/5dc438d2-e138-4db0-97a0-e5ae8c3473e8)

# Introduction
Before doing data analysis, we have to do data processing. It is always a good practice to verify your data preprocessing before you start your analysis.

The dataset of "Top 2000 Universities of the World" has been provided in the link below.
<img width="452" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/981bea99-9bb1-4c81-bf3e-d10dfd7cb3ff">

https://drive.google.com/file/d/1C0jgmQlO5xps06WOalrnrbmZ_l2tclgU/view?usp=sharing

## Import dataset
https://colab.research.google.com/drive/1S-Z0yBo5T4rZ6CZAbP7mbag49dducyY_?usp=sharing
```
import pandas as pd
df=pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Top 2000 Universities of the World.csv")
df.head()
```
<img width="452" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/7e186e95-eed5-40f6-89e5-33a6e5a19a23">

## Data Processing
After having looked at the dataset, it is expected that null or NA values are verified within the dataset, and the corresponding rows are to be dropped as needed to prepare the data for analysis.

Count of Null / NA values:
```
df.isnull().sum()
```

<img width="266" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/5e3dd0e7-cd3f-4d9c-8b48-60d3cd7a25d7">

![rainbow](https://github.com/Winxent/portfolio/assets/146320825/5dc438d2-e138-4db0-97a0-e5ae8c3473e8)

# Size / Shape of Dataset
After verifying the data for missing values and formulating our research questions. We always observe our dataset, describe it and check the dimensions of the dataset.

Data description provides us a quick view of the data columns and the recorded values in our dataset. We need to make a quick view of our dataset to see how many rows, columns we have in our dataset, and how the data is distributed.

```
df.shape
```
Number of Rows: 2000
Number of Columns: 9
```
df.info
```
Number of Categorical Columns: 2
Number of Numerical Columns: 7

<img width="458" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/57526384-53a4-4ffe-bda3-b3251bc4cb26">

```
df.describe()
```
<img width="458" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/c954a19e-35c1-418e-9760-2fcd27dddac7">

![rainbow](https://github.com/Winxent/portfolio/assets/146320825/5dc438d2-e138-4db0-97a0-e5ae8c3473e8)

# understanding our dataset columns
As a data analyst, after having the initial description of the dataset, we need to understand the columns in the dataset so that we can choose our data aggregation and data summary strategies accordingly for generating insights from our dataset.

We will do some analysis for 4 of the data columns
1.	Type (Numerical, Categorical) of each column,
2.	the description of each column, and
3.	values in each column (list out 3 sample values for categorical column, and the range of value for numerical values)

<img width="452" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/ad4de900-a0b3-499d-90f4-e7fe78ca3ccc">

![rainbow](https://github.com/Winxent/portfolio/assets/146320825/5dc438d2-e138-4db0-97a0-e5ae8c3473e8)

# Analysis
A student wants to get into the best university. This dataset provides us information about the Universities and their world ranking of different areas (e.g. Employment, Research etc.).

Let’s he/she you want to find a university that has good alumni employment opportunities. From the dataset given,
  * list out the top 10 universities based on employment ability
  * list out the countries where these universities come from
    
using data aggregation strategies such as sorting, filtering etc.

## Top 10 Universities
```
df_work = df.filter(["World Rank","Institution", "Country", "Alumni Employment Rank"])
sorted_df = df_work.sort_values(by=['Alumni Employment Rank'] , ascending= True )
sorted_df.head(10)
```

<img width="458" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/c032f576-ff93-4018-a8bc-99dc1288d59c">

## Distinct Countries Count and their Names
```
sorted_df["Country"].head(10).nunique()
```
7
```
sorted_df["Country"].head(10).unique()
```
'China', 'USA', 'Greece', 'Egypt', 'Hungary', 'Bulgaria', 'Spain'

# Subset Analysis
While performing Data Analysis, we might not need to consider all the rows and columns. For example, if we want to have a high level overview of the universities in the USA based on their world rank and overall scores, we can make a subset of data having World Rank, Score and Institution only. We can also further filter out universities that are not in the USA.

To achieve that, below steps have taken
1.	Create a subset data frame using filters on above mentioned columns
2.	And from this subset, filter out the Universities which belong to the USA (the output data frame should only contain universities from the USA).

## Mention the name of top 5 and bottom 5 universities of USA:

1. Create a filtered variable.
```
df_score = df.filter(["World Rank","Institution", "Country", "Score"])
df_score.head()
```
2. Sort the filtered variable.
```
sorted_df_score = df_score.sort_values(by=['Score'] , ascending= False )
Display the result in the country USA
sorted_df_score[(sorted_df["Country"] == "USA")].head(5)
```
### Top 5: 

<img width="458" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/e69487af-c653-4838-952a-cf755c49924c">

### Bottom 5:

<img width="458" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/95050a75-5a72-4e36-b557-b69905e150ff">


# Group by country 
Next, we would like to analyse which countries are having more high ranking and high quality universities and which countries have less.

In order to generate these insights, we are required to make a summarised data frame with all the countries and their average score of the universities. (Hint: consider using the “groupby” function)

Create a group by table for country then include the mean function
```
grouped_df = df.groupby('Country')
grouped_df.mean()
```
<img width="458" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/05c43e8f-c1ec-4437-9f60-a1eadcd90cea">

By using the filter function in google collaboratory, we can find and filter for each individual country
The average score of
1.	Ireland:72.02
2.	United Kingdom:73.63
3.	Pakistan: 68.38
4.	Germany: 74.47

Two lowest performing countries: 
1.	North Macedonia
2.	Kazakhstan

# IQR of Dataset

We have studied the Ranges, Quartiles and Interquartile range in detail. We can use it to help us in finding the outliers in the university dataset (i.e. those extremely good or bad universities).

In order to perform this analysis, we will use the 1.5IQR method 

1. Identification of Column of interest:
```
Score
```
2. Minimum and Maximum of column used in Analysis:
```
df["Score"].min()
df["Score"].max()
```
65.7, 100.0

3. Q1, Q3 and IQR of the column:
```
q1, q3 = df["Score"].quantile([0.25,0.75])
q1,q3
```
(67.7, 74.1),
```
iqr = q3- q1
iqr
```
6.40

4. Write down the lower and upper expected minimum and maximum of IQR (3 point):
```
lower_min = q1 - (1.5*iqr)
upper_max = q3 + (1.5*iqr)
print("Lower expected min of IQR = ", lower_min)
print("Upper expected max of IQR = ", upper_max)
```
Lower expected min of IQR =  58.100000000000016
Upper expected max of IQR =  83.69999999999999

5. Number of outliers identified (1 point) 
```
df[(df["Score"] > 83.69999999999999) | (df["Score"] < 58.100000000000016 )]
```
<img width="458" alt="image" src="https://github.com/Winxent/University-Ranking/assets/146320825/3627e13f-8f47-42c1-8028-d7991d0c68b3">
63 outliers found

6. Any insights that you can conclude from this analysis 
Taking help from the Interquartile Range, we have identified 63 Institutions scored higher than the maximum of IQR or the Upper bound threshold of data distribution. 
63 universities score higher than the max interquartile range. 










