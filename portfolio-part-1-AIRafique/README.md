# Analysis of an E-Commerce Dataset

## About

*I, the student, shall henceforth be refered to as "The Author"*

This repository contains the project for portfolio part 1.
Also included in the repository:
- [dataset](/data/The%20E-commerce%20Dataset.csv)
- [dataset explanation](/resources/Fig1%20The%20Combined%20E%20commerce%20Dataset.png)

## Introduction

The project is based on Jupyter Notebook, a web-based notebook environment for interactive computing, and uses python libraries **pandas** and **matplotlib** in order to properly process and analyse the given dataset. We have been provided with a combined e-commerce dataset. In this dataset, each user has the ability to post a rating and review for the products they purchased. Additionally, other users can evaluate the initial rating and review by expressing their trust or distrust. The project serves as an assignment and answers questions based on the dataset.

<img src="resources/Fig1 The Combined E commerce Dataset.png" width="500"/>


### Cleaning the Data-Set

The initial [task](Portfolio_1_questions.ipynb#Q1) involved removing all rows that had any missing data. Missing, in this context meant any null values in the fields `gender`, `rating`, `helpfulness`, or any row with `'none'` in review. 

This was an easy enough task to accomplish for the author, just using `dropna()` function from the pandas library to drop any rows with NaN (Not a Number) values in the given fields from the table. For the review field, the author decided to use the  `loc()` function to index any field with a specific string and then drop the selected fields.

### Descriptive Statistics

The next [task](Portfolio_1_questions.ipynb#Q2) revolved around descriptive statistics of the cleaned data. The author used the function `nunique()` to find the number of unique users, reviews, items, and categories. To output descriptive statistics e.g., mean, std, max, and min of each field, df[field name].describe() was used. The function groupby(value) was used to sort the field in separate groups for ease of analysis.

### Plotting and Analysis

This [task](Portfolio_1_questions.ipynb#Q3) focused on plotting and exploring correlation between gender/helpfulness/category and
ratings. The task proved to be very challenging since it was left open-ended for the author to decide which plot would work best for each relation. 

After careful consideration, and multiple attempts, the author finally settled on using 4 plots for each correlation to showcase their differences in as much detail with as little clutter as possible. A bar plot and a line chart showing the count of users per gender/helpfulness/category for every possible rating were the obvious choices to be used. Any layman can use and understand these plots to differentiate between each group in a field. 

The box-plot was a tricky choice because it deals with quartiles instead of simple averages. Harder for a layman but more descriptive for a technically sound mind to infer data. Matplotlib's `seaborn` library was useful for this plot.

Finally, a bar plot showing the mean rating for each group of every field. This was a logical decision for the author, and it is exemplified by the following image. The data from this plot goes hand-in-hand with data from the bar and line graphs to provide complete information.

<center><img src="resources/Online Reviews.png" width="300"/><center>

The author provided some insights on every plot and then a brief summary of the overall information gained from performing this task.

### Outlier Detection and Removal

The [task](Portfolio_1_questions.ipynb#Q4) for removing any outliers based on the provided parameters proved to be trickier than the author first thought. 

The first attempt was straightforward indexing all the outliers and removing them from the dataframe, one field at a time. However, it soon became apparent that this was not the correct approach. Removing outliers from one field resulted in creating outliers in another field that the author had previously cleaned. For example, if we were to first remove all reviews from users that have rated less than 7 items and then remove items which have received less than 11 ratings, then it may result in creating more users that have rated less than 7 items in the remaining list.

To overcome this, an iterative approach was adopted. The author wrote a function and ran a loop on the dataset until no more outliers were found i.e. the size of previous and current datasets were the same. In hindsight, this would seem obvious but it was challenging for the author.

At the end, the author read the announcements which stated clearly that a linear approach approach was to be adopted hence that was kept in the final version.

### Conclusion

The author feels that the portfolio tasks have indeed helped in expanding their knowledge of data analysis techniques and the use of technology in simplifying these tasks. It has also made the author more aware of the importance of minute details in a large pile of data.




