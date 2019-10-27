---
title: "SQL Joins"
tags:
  - sql
  - joins
  - database
date: "2019-10-27T05:44:08.920Z"
layout: post
---
#### Author: [Kimberly Collins](https://github.com/kacollins)

## Database Normalization
* Separate data into different tables
* Usually represent each entity with an ID
* Optimize for data storage efficienty, not human readability

## Purposes of Joins
* Use data from multiple tables
* "Un-normalize" data
  * Make data human readable
  * View information about the entity, not just the ID

## How to Get Started
* Install SQL Server Management Studio or another query tool (maybe LinqPad!)
* Install AdventureWorks sample database

## Types of Joins

### [CROSS JOIN](https://clips.twitch.tv/HelpfulRelatedMarrowMikeHogu)
* Usage
  * Returns all possible combinations of rows between two tables
  * If one table has 2 rows and the other has 3 rows, cross joining them returns 6 rows
  * Used for generating test data and for reports
  * Otherwise, use it as a last resort
* Example
  * Department table has 16 rows
  * Shift table has 3 rows
  * CROSS JOIN will return the 48 possible combinations

### [INNER JOIN](https://clips.twitch.tv/UnsightlyRichDogeDuDudu)
* [Usage](https://clips.twitch.tv/AmusedGracefulLampRickroll)
  * Returns rows that match on criteria
  * Can (unintentionally) limit results or introduce duplicates
  * "INNER" is optional but recommended
  * Generally joining tables on one or more columns that exist in both
    * Usually the primary key in one table and a foreign key in the other
    * Other criteria can be used
* Example
  * ProductSubcategory table has a column for ProductCategoryID
  * We want to see the name of the product category for each subcategory, not the ID

### [LEFT OUTER JOIN](https://clips.twitch.tv/PlumpGoldenDaikonStrawBeary)
* Usage
  * Returns rows in the first table even if they don't have a match in the second table
  * Can unintentionally introduce duplicates
  * "OUTER" is optional
  * Often used with a WHERE clause to only get the rows in the first table that don't have a match in the second table
* Examples
  * Show the subcategory for each product, if it has one
  * Get the products that have never been sold (with WHERE clause)

### RIGHT OUTER JOIN
* Analogous to LEFT OUTER JOIN
* Rarely used

### FULL OUTER JOIN
* Usage
  * Returns rows from both tables even if they don't have matches in the other
  * "OUTER" is optional
  * Often used for comparison reports
* Example
  * Show salespeople assigned to each territory
  * Include salespeople not assigned to any territory
  * Include territories without any salespeople assigned

## Learning More
  * [Slides](https://docs.google.com/presentation/d/1JzqXzFljkzZ5gTVrgzIV7Hhgv70Ffpi2unwnNWxbyjE/edit)
  * [Video](https://www.youtube.com/watch?v=2IGQFucnGR4)
  * [Examples](github.com/kacollins/intro-to-sql-joins)
  * OKC SQL meetup group - meets on the third Monday evening of the month
  * Techlahoma's Slack
    * Sign up at slack.techlahoma.org
    * #databases and #okcsql channels
    * @kimberlycollins

-- [Kimberly](https://github.com/kacollins)
