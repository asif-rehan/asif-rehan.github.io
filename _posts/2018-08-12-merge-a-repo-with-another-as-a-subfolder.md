---
id: 124
title: 'Merge a repo with another as a subfolder'
date: '2018-08-12T19:03:50+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=124'
permalink: /merge-a-repo-with-another-as-a-subfolder/
categories:
    - System
---

Sometimes we may end up with one main repository and another independently developed repository for a new feature. Later it may turn out, that the independent repo needs to become a part of the main repo as a subfolder.

To do that, we can use the git command using subtree. We need to put the new subfolder name and voila!

```
git subtree add --prefix=new_subdirectory_name git://github.com/userid/main_repo.git project_branch_name
```