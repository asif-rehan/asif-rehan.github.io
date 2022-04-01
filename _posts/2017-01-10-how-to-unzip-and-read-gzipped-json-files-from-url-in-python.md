---
id: 145
title: 'How to unzip and read gzipped JSON files from URL in Python'
date: '2017-01-10T19:13:24+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=145'
permalink: /how-to-unzip-and-read-gzipped-json-files-from-url-in-python/
categories:
    - Linux
    - System
---

## The Problem

Sometimes we end up zipping JSON files and putting up somewhere on the interweb. Now we need to read it back from the HTTP server and parse the file using Python. For that situation, let us assume that the zipped JSON is located at this URL:  
`http://example.com/python_list_turned_into.json.gz`. To read this file, we need to do the following

– Fetch the file using `urllib2`  
– Add a header which will be used to detect the `gzip` format  
– Then open the file and read the compressed file  
– Next, uncompress the file using `gzip` library and load it!

That’s it!

## The Python Code

Let’s look at the code snippet below, which does exactly what we need.

```
<pre class="line-numbers">```python

import urllib2
import json
import gzip
import StringIO

def unzipper(url="http://example.com/python_list_turned_into.json.gz"):

    request = urllib2.Request(url)
    request.add_header('Accept-encoding', 'gzip')
    opener = urllib2.build_opener()
    f = opener.open(request)
    compresseddata = f.read()
    compressedstream = StringIO.StringIO(compresseddata)
    gzipper = gzip.GzipFile(fileobj=compressedstream)
    data = gzipper.read()
    list_output = json.loads(data)
    
    return list_output
```
```