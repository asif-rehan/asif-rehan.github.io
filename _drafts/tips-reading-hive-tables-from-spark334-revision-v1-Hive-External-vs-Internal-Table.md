---
id: 337
title: 'Hive External vs Internal Table'
date: '2020-06-24T02:34:52+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/334-revision-v1/'
permalink: /334-revision-v1/
---

For external tables, use

```
<pre class="wp-block-preformatted">spark.sql()
```

  
For internal/managed tables, use

```
<pre class="wp-block-preformatted"> hive.executeQuery() 
```