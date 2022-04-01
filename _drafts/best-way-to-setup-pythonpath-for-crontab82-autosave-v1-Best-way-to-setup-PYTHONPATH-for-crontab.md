---
id: 196
title: 'Best way to setup PYTHONPATH for crontab'
date: '2018-08-13T12:32:34+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/82-autosave-v1/'
permalink: /82-autosave-v1/
---

There are many suggestions on this.

Add PYTHONPATH at the end of the ~/.bash\_profile or ~/.bash\_login files. If they do not exist, add it to ~/.bash\_profile as suggested by [this StackOverflow post](https://web.archive.org/web/20170607032258/http://stackoverflow.com/questions/3402168/permanently-add-a-directory-to-pythonpath).

```
<span style="font-family: Consolas, Monaco, monospace;">export PYTHONPATH="${PYTHONPATH}:/home/path/to/your/python/package/"</span>
```

But this will add the package to the current user’s PYTHONPATH. To ensure crontab gets it right away. add this line to the top of crontab file, BEFORE crontab tries to execute any script of that package

```
PYTHONPATH/home/path/to/your/python/package
```