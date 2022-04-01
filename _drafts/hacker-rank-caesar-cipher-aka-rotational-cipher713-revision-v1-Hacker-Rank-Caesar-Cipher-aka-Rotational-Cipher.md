---
id: 753
title: 'Hacker Rank: Caesar Cipher aka Rotational Cipher'
date: '2022-03-20T17:23:50+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/713-revision-v1/'
permalink: /713-revision-v1/
---

This is a array/string problem and you can look up this problem on [HackerRank](https://www.hackerrank.com/challenges/caesar-cipher-1).

To solve this one, it can not theoretically be any better than O(n) time complexity. Here I convert the string to character array, then for each character and if this is a small ASCII character between a-z, then subtract the value of a, and add the offset values, take modulus of 26 and add back the value of 26. This primitive integer value has to be cast to char value before replacing the original character.

Similar logic applies for capital case characters, A-Z. At this point, it deviates from the HackerRank problem as I consider numbers as well for encryption, where the modulus of 10 is taken.

The solution below is pretty self-explanatory.

## Java Solution 

```
<pre class="wp-block-code" title="Rotational Cipher">```
class Main {

  // Add any helper functions you may need here
  

  String rotationalCipher(String input, int rotationFactor) {
    char[] chars = input.toCharArray();
    for (int i=0; i<chars.length; i++) {
      rotate(i, chars, rotationFactor);
    }
    
    return String.valueOf(chars);
  }

  void rotate(int i, char[] chars, int rf) {
    char c = chars[i];
    char newCh;
    
    if (c >= 'a' && c <= 'z') {
      newCh = (char)((c-'a' + rf) % 26 + 'a');
    } else if (c >= 'A' && c <= 'Z') {
      newCh = (char)((c-'A' + rf) % 26 + 'A');
    } else if (c >= '0' && c <= '9') {
      newCh = (char)((c-'0' + rf) % 10 + '0');
    } else {
      return;
    }  
    chars[i] = newCh;
    
    return;
  }

```
```