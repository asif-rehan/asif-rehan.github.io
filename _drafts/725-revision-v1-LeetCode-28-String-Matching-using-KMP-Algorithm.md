---
id: 726
title: 'LeetCode 28: String  Matching using KMP Algorithm'
date: '2021-11-06T03:55:22+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/725-revision-v1/'
permalink: /725-revision-v1/
---

A typical string search within string involves either a naive solution where we use two pointers. One for the “needle” string and the other for the “haystack” string. Starting from each character in haystack, we compare every character in needle with the character in haystack. If all the characters in needle are found in haystack, then we return true. If one of the character does not match, then we take the next character in the haystack, and restart at the beginning of the needle string. This results in a O(mn) algorithm, where m = length of haystack string, n = length of needle string. Could we do any better?

Yes, use the KMP algorithm. This uses a trick called prefix-suffix array, which helps skip some parts of the string in haystack that we already know repeat in the needle array. KMP algorithm results in linear O(m+n) time complexity at the expense of a bit extra memory for the prefix array.

First, check out this [tutorial in YouTube](https://www.youtube.com/watch?v=5i7oKodCRJo) which has a very nice animation to explain the basic idea. But the code example in the video uses 1-based index. So let us follow this Java implementation below for easier undestading:

```
<pre class="wp-block-code">```java
    public int strStr(String haystack, String needle) {
        if (haystack==null || needle==null) return 0;
        char[] text = haystack.toCharArray();
        char[] pattern = needle.toCharArray();

        if (pattern.length==0) return 0;
        if (text.length==0) return -1;

        int[] prefixSuffix = prefixSuffix(pattern);
        int i = 0;
        int j = 0;
        while(i<text.length && j<pattern.length) {
            if (text[i] == text[j]) {
                i++;
                j++;
            } else {
                if (j==0) {
                    i++;
                } else {
                    j = prefixSuffix[j-1];
                }
            }
        }
        if(j==pattern.length) {
            return true;
        }
        return false;

    }

    int[] prefixSuffix(char[] pattern) {
        int[] pre = new int[pattern.length];
        pre[0] = 0;
        
        int j = 0;
        for (int i=1; i<pattern.length; i++) {
            while (j>0 && pattern[i]!=pattern[j]) {
                j = pre[j-1];
            }
            if (pattern[i]==pattern[j]) {
                j++;
            }
            pre[i] = j;
        }
        return pre;
    }
```
```