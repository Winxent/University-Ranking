# University-Ranking
Goal: Data analysis using google collaboratory python pandas on university ranking dataset

https://colab.research.google.com/drive/1S-Z0yBo5T4rZ6CZAbP7mbag49dducyY_?usp=sharing

![rainbow](https://github.com/Winxent/portfolio/assets/146320825/5dc438d2-e138-4db0-97a0-e5ae8c3473e8)

# Introduction
Before doing data analysis, we have to do data processing. It is always a good practice to verify your data preprocessing before you start your analysis.

The dataset of "Top 2000 Universities of the World" has been provided in the link below.

https://drive.google.com/file/d/1C0jgmQlO5xps06WOalrnrbmZ_l2tclgU/view?usp=sharing

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





