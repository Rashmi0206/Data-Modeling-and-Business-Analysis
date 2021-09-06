# Data Model and Business Analysis

# 1. Review Existing Unstructured Data and Diagram a New Structured Relational Data Model

Review the 3 sample data files provided below. Develop a simplified, structured, relational diagram to represent how you would model the data in a data warehouse. The diagram should show each table’s fields and the joinable keys. 

## Solution:

I have ingested the 3 data files and processed the data in part 1 of [data processing and sql queries](https://github.com/Rashmi0206/Data-Modeling-and-Business-Analysis/blob/main/Data%20processing%20and%20Sql%20Queries.ipynb) notebook.

Based on the data dictionary provided and the structure of the files, I have created 4 tables that can be joined based on below ER diagram.

![alt text](https://github.com/Rashmi0206/User-Analysis/blob/main/Database%20ER%20diagram%20(crow's%20foot).png?raw=true)


# 2.Write a query that directly answers a predetermined question from a business stakeholder
Write a SQL query against your new structured relational data model that answers one of the following bullet points below of your choosing. Commit it to the git repository along with the rest of the exercise.
Note: When creating your data model be mindful of the other requests being made by the business stakeholder. If you can capture more than one bullet point in your model while keeping it clean, efficient, and performant, that benefits you as well as your team.


* What are the top 5 brands by receipts scanned for most recent month?
* How does the ranking of the top 5 brands by receipts scanned for the recent month compare to the ranking for the previous month?
* When considering average spend from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?
* When considering total number of items purchased from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?
* Which brand has the most spend among users who were created within the past 6 months?
* Which brand has the most transactions among users who were created within the past 6 months?

## Solution

Based on the data issues with barcode field in the receipt_item_list table that is causing problem in joining with brands table ( this is explained in detail in part 2 of [data processing and sql queries](https://github.com/Rashmi0206/Data-Modeling-and-Business-Analysis/blob/main/Data%20processing%20and%20Sql%20Queries.ipynb) notebook), I decided to work on below questions:

* When considering average spend from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?
* When considering total number of items purchased from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?

Please find the solution in Part 2 of [data processing and sql queries](https://github.com/Rashmi0206/Data-Modeling-and-Business-Analysis/blob/main/Data%20processing%20and%20Sql%20Queries.ipynb) notebook.

# 3.Evaluate Data Quality Issues in the Data Provided
Using the programming language of your choice (SQL, Python, R, Bash, etc...) identify at least one data quality issue. We are not expecting a full blown review of all the data provided, but instead want to know how you explore and evaluate data of questionable provenance.

Commit your code and findings to the git repository along with the rest of the exercise.

## Solution

# 4.Communicate with Stakeholders
Construct an email or slack message that is understandable to a product or business leader who isn’t familiar with your day to day work. This part of the exercise should show off how you communicate and reason about data with others. Commit your answers to the git repository along with the rest of your exercise.

* What questions do you have about the data?
* How did you discover the data quality issues?
* What do you need to know to resolve the data quality issues?
* What other information would you need to help you optimize the data assets you're trying to create?
* What performance and scaling concerns do you anticipate in production and how do you plan to address them?

## Solution:


# About The Data
## Receipts Data Schema
_id: uuid for this receipt

bonusPointsEarned: Number of bonus points that were awarded upon receipt completion

bonusPointsEarnedReason: event that triggered bonus points

createDate: The date that the event was created

dateScanned: Date that the user scanned their receipt

finishedDate: Date that the receipt finished processing

modifyDate: The date the event was modified

pointsAwardedDate: The date we awarded points for the transaction

pointsEarned: The number of points earned for the receipt

purchaseDate: the date of the purchase

purchasedItemCount: Count of number of items on the receipt

rewardsReceiptItemList: The items that were purchased on the receipt

rewardsReceiptStatus: status of the receipt through receipt validation and processing

totalSpent: The total amount on the receipt

userId: string id back to the User collection for the user who scanned the receipt


## Users Data Schema

_id: user Id

state: state abbreviation

createdDate: when the user created their account

lastLogin: last time the user was recorded logging in to the app

role: constant value set to 'CONSUMER'

active: indicates if the user is active; only Fetch will de-activate an account with this flag

## Brand Data Schema

_id: brand uuid

barcode: the barcode on the item

brandCode: String that corresponds with the brand column in a partner product file

category: The category name for which the brand sells products in

categoryCode: The category code that references a BrandCategory

cpg: reference to CPG collection

topBrand: Boolean indicator for whether the brand should be featured as a 'top brand'

name: Brand name

