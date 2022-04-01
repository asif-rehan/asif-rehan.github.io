---
id: 130
title: 'Merge a repo with another as a subfolder'
date: '2018-08-12T19:03:53+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/124-autosave-v1/'
permalink: /124-autosave-v1/
---

Sometimes we may end up with one main repository and another independently developed repository for a new feature. Later it may turn out, that the independent repo needs to become a part of the main repo as a subfolder.

To do that, we can use the git command using subtree. We need to put the new subfolder name and voila!

```
git subtree add --prefix=new_subdirectory_name git://github.com/userid/main_repo.git project_branch_name
```