---
id: 745
title: 'Checking SHA256 Checksum One Line Command'
date: '2022-02-22T17:18:00+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=745'
permalink: /checking-sha256-checksum-one-line-command/
categories:
    - Linux
    - System
tags:
    - Checksum
    - Linux
    - SHA256
---

Just do the following

```
<pre class="wp-block-code">```
cd /folder/path
echo "known_sha_code  filename"  | sha256 --check
```
```

yup, that’s it.

Example:

```
<pre class="wp-block-code">```
user@user-Linux:~$ echo "4ee9c3aa53329cd7...d362b4 Miniconda3-py39_4.11.0-Linux-x86_64.sh" | sha256sum --check
Miniconda3-py39_4.11.0-Linux-x86_64.sh: OK
```
```