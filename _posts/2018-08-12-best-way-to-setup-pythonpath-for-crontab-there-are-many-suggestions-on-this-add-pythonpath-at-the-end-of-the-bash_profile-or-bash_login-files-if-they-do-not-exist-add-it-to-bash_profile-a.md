---
id: 118
title: 'How much memory does importing PANDAS library take?'
date: '2018-08-12T19:10:06+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=118'
permalink: /best-way-to-setup-pythonpath-for-crontab-there-are-many-suggestions-on-this-add-pythonpath-at-the-end-of-the-bash_profile-or-bash_login-files-if-they-do-not-exist-add-it-to-bash_profile-a/
categories:
    - 'Data Science'
---

<article class="post-94 post type-post status-publish format-standard hentry category-python category-uncategorized tag-memory-management tag-pandas tag-performance tag-python" id="post-94"><div class="entry-content">## Objective

Let us compare the memory consumption of Python PANDAS library.

## Methodology

Small script called memtest*.py*:

```
<pre class="line-numbers">```python

@profile
def a():
    import pandas

if __name__=="__main__":
    a()

```
```

Test it with

```bash
$python -m memory_profiler memtest.py
```

## Results:

Output:  
![](https://asifrehan.com/wp-content/uploads/2018/08/memory-profiling-300x104.png)

The increment of memory usage in line#4 shows, it took 36.527MB to import pandas on my machine. What does your benchmarking result look like?

</div></article>