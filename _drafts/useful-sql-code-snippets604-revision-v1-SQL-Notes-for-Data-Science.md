---
id: 639
title: 'SQL Notes for Data Science'
date: '2021-03-16T19:36:21+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/604-revision-v1/'
permalink: /604-revision-v1/
---

SQL is one of the most widely used programming language but yet it remains too much undervalued. Here is some quick SQL query snippets for refreshing the memory.

## Introductory Concepts

**Optional:** Learn about `FOREIGN KEY` and `PRIMARY KEY` and the different Database Normalization types from this [Wikipedia page](https://en.wikipedia.org/wiki/Database_normalization#Normal_forms). Probably you will need only up to 1st to 4th Normal Form of a database.

These basic concepts are useful to understand why we need table joins. But not entirely essential.   
  
Also this note does not talk about creating database schema and modifying it.

#### Basic SQL Syntax

In the example below, you are querying two columns, `column_name_1, column_name_2` from the `table` but we only want the unique values from the second column, so we use `DISTINCT`. The conditions to select particular data are added in the `WHERE` clause. The two selected columns are then sorted first by ascending order and then by descending order using the `ORDER BY` clause. And finally we are only interested in maximum 10 rows.

```
<pre class="wp-block-code">```
SELECT column_name_1, DISTINCT(column_name_2)
FROM table_name
WHERE column_name_1 = "abc" and column_name_2 = "xyz" 
ORDER BY column_name_1 ASC, column_name_2 DESC
LIMIT 10
```
```

#### Case When

Another simple clause is CASE WHEN which is useful as a if-else block. Between a `CASE ... END` There can be as many `WHEN` block and then one `ELSE` clause

```
<pre class="wp-block-code">```
CASE
    WHEN condition_1 THEN result_1
    WHEN condition_2 THEN result_2
    ELSE final_value
END
```
```

#### Union vs Union All

Union enables stacking two table with same columns one on top of the other. `UNION` only keeps distinct rows from two tables, on the other hand `UNION ALL` keeps all rows.

## Intermediate Difficulty

#### Aggregate Functions, `HAVING` clause

Aggregate functions are basically statistical summary functions like SUM(), MIN(), MAX(), AVG() etc. See the section titled “Rank, Window, Lag, Lead” below.

#### `OVER()`, `PARTITION BY`

From [SQLShack.com](https://www.sqlshack.com/sql-partition-by-clause-overview/) “In the SQL GROUP BY clause, we can use a column in the select statement if it is used in Group by clause as well. It does not allow any column in the select clause that is not part of GROUP BY clause”. Definitely check out the link to get a clear idea about these useful clauses and their differences.

#### Table Joins

Joins are very intuitive but may become quite complex especially when used with nested sub-queries.

There are various types of SQL joins. Cross join simply makes all the combinations of the two tables as shown in the image from [SQLShack.com](https://www.sqlshack.com/sql-cross-join-with-examples/). You should check out their post on Cross join, it is very detailed!

<figure class="wp-block-image size-large">![](https://www.sqlshack.com/wp-content/uploads/2020/02/sql-cross-join-working-mechanism.png)<figcaption>[SQLShack.com](https://www.sqlshack.com/sql-cross-join-with-examples/) has excellent explanation on Cross Join</figcaption></figure>Cross Join can be run by this example where `table_name_1` and `table_name_2` are cross joined. This is often time very inefficient. So be careful with cross joins and look out for ways to avoid it.

```
<pre class="wp-block-code">```
SELECT column_name_1, column_name_2
FROM table_name_1,table_name_2 
```
```

I find this image below to explain the SQL joins very effective

<figure class="wp-block-image size-large">![](https://i.stack.imgur.com/qje6o.png)<figcaption>Image: SQL Joins explained by [Lasse V. Karlssen on Stackoverflow](https://stackoverflow.com/a/406333)</figcaption></figure>[Carsson Forter writes](https://towardsdatascience.com/how-to-ace-data-science-interviews-sql-b71de212e433), “**By filtering and aggregating your data before joining, you write the most efficient SQL.** Joins are expensive to process so you want the fewest possible rows before joining two tables together… if you have a `JOIN` and a `WHERE` clause in the same CTE, SQL processes the `JOIN` first”.   
  
So trying to filter and then joining is typically more efficient. That brings us to more advanced topics, including subqueries and CTEs.

### Advanced Syntax

#### Common Table Expressions (CTE)

CTEs gives a way to store some queried data with a name so that it can be used in more complex queries. That way, CTEs help write complex SQL queries in a cleaner way.

CTEs commonly have this syntax, you can have multiple CTE’s. [Source here](https://stackoverflow.com/a/584320)

```
<pre class="wp-block-code">```
WITH 
    cte1 as (SELECT * from table WHERE ...),
    cte2 as (SELECT * from table WHERE ...)
select * from cte1 union select * from cte2
```
```

[This article by Carsson Forter](https://towardsdatascience.com/how-to-ace-data-science-interviews-sql-b71de212e433) provides a great example of using multiple CTEs to calculate the avg time between two transactions of a customer. This is his example which also used `group by` clause to aggregate data by user name.

```
<pre class="wp-block-code">```
-- First, find all of user_a's transactions today 
with user_a_trans as (
  SELECT username, time
  FROM transactions
  WHERE day = '2017-09-08'
  AND username = 'user_a'),

-- Join each transaction to all transactions occurring after it

joined_trans as (
  SELECT username, time, future_times
  FROM user_a_trans a
  INNER JOIN user_a_trans b
  ON b.time > a.time),

-- Find the immediate next transaction using MIN()
next_trans as (
  SELECT username, time, MIN(future_times) as next_time
  FROM joined_trans
  GROUP BY username, time)

-- Average difference of the time and the next transaction's time
SELECT AVG(next_time - time) as avg_time_to_next_transaction
from next_trans;
```
```

#### Rank, Window, Lag, Lead

The Window clause is useful to set a condition over which data is split. `WINDOW` can be at a single location and referred to while calling aggregation functions like `SUM()` and `AVG()`. This is the [link for the code below](https://www.postgresql.org/docs/9.1/tutorial-window.html).

```
<pre class="wp-block-code">```
SELECT sum(salary) OVER w, avg(salary) OVER w
  FROM empsalary
  WINDOW w AS (PARTITION BY depname ORDER BY salary DESC);
```
```

For `LAG`, see a thorough explanations [here](https://www.sqlshack.com/sql-lag-function-overview-and-examples/). The same logic applies on `LEAD`

For rank functions, `ROW_NUMBER()`, `RANK(),` and `DENSE_RANK()`, see [this resource](https://www.sqlshack.com/overview-of-sql-rank-functions/).

#### FIRST\_VALUE and LAST\_VALUE

A good example of these functions is found on [this website](https://docs.microsoft.com/en-us/sql/t-sql/functions/first-value-transact-sql?view=sql-server-ver15). Copying the example query here

```
<pre class="wp-block-code">```sql
USE AdventureWorks2012;   
GO  
SELECT JobTitle, LastName, VacationHours,   
       FIRST_VALUE(LastName) OVER (
                   PARTITION BY JobTitle   
                   ORDER BY VacationHours ASC  
                   ROWS UNBOUNDED PRECEDING  ) 
        AS FewestVacationHours  
FROM HumanResources.Employee AS e  
INNER JOIN Person.Person AS p   
    ON e.BusinessEntityID = p.BusinessEntityID  
ORDER BY JobTitle;
```
```

## Geospatial SQL Queries

This is another important group of SQL queries practically useful but not talked about in most cases.