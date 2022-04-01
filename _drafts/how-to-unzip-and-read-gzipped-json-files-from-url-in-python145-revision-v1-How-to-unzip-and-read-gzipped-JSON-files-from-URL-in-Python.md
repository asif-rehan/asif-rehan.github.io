---
id: 436
title: 'How to unzip and read gzipped JSON files from URL in Python'
date: '2020-11-11T04:38:51+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/145-revision-v1/'
permalink: /145-revision-v1/
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