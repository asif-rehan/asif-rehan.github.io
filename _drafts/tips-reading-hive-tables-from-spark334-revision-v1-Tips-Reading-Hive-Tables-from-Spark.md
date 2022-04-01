---
id: 420
title: 'Tips: Reading Hive Tables from Spark'
date: '2020-11-10T19:47:34+00:00'
author: 'Asif Rehan'
excerpt: 'Collection of useful tips when working with Big Data tools including Hadoop, Hive, Spark'
layout: revision
guid: 'https://asifrehan.com/334-revision-v1/'
permalink: /334-revision-v1/
---

<figure class="wp-block-image size-large" data-amp-lightbox="true" data-amp-noloading="true">![Hadoop Hive Apache Spark Big Data Warehouse Ecosystem](https://asifrehan.com/wp-content/uploads/2020/11/image.png)</figure>## Tip#1. **Solving Access Permission Conundrum** 

After creating a new database in Hive, you only need Hive ranger policy to allow reading the tables in the new database from Hive/Beeline/Beeline-Ranger.  
  
But when reading the Hive table from Spark, it also needs a HDFS permission policy, in addition to the Hive ranger policy as above.

## Tip#2. **Running Queries on Hive Tables**

For internal/managed ACID tables, use

```
<pre class="wp-block-preformatted"> hive.executeQuery("SELECT * FROM DB.TABLE") 
```

For external non-ACID tables, use this below instead of over `hive.executeQuery() ` to get 10x performance increase

```
<pre class="wp-block-preformatted">spark.sql("SELECT * FROM DB.TABLE")
```

## Tip#3. Check if a Table is Managed or External

Now if you are wondering if a table is managed or external, you can run this below in Hive/Beeline/Beeline-ranger which tells you if a table is external or managed table

```
<pre class="wp-block-preformatted">DESCRIBE FORMATTED db.table_name;
```

It should show the information regarding the table. Check the Table Type value it should either say Table Type: `MANAGED_TABLE` or `EXTERNAL_TABLE `