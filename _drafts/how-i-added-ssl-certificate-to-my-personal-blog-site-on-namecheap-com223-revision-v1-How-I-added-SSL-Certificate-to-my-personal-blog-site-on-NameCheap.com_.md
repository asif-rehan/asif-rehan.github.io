---
id: 225
title: 'How I added SSL Certificate to my personal blog site on NameCheap.com'
date: '2020-02-17T15:34:27+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/223-revision-v1/'
permalink: /223-revision-v1/
---

This blog site is currently hosted using the managed WordPress hosting called EasyWP available on NameCheap.com. Though there are many hosting services that integrate with the free Let’s Encrypt SSL tool, NameCheap does not seem to have any plan to do that. Instead NameCheap asks you to pay $8.88 per year for the basic SSL Certificate for the lock sign in front of the address bar in the browser when your website it accessed. Google and other search engines discourage visitors from visiting sites which does not have SSL cerficates for obvious security reasons. But there are free options to get a basic SSL certificate for your website. Many online articles describe the steps to get the certificate and install it through the CPanel.

However, as I figured through a chat with a customer service representative on NameCheap, that users only using EasyWP on NameCheap do not get access to CPanel. So adding SSL certificate manually through CPanel does not work. Instead what worked for me is [SSL for Free](https://www.sslforfree.com/create?) which allows you to generate a free SSL certificate, a CA Certificate and a public key when you select manual verification. Just follow the steps on *SSL for Free.* Since this website already has a nice post to help you through the simple process, I am just sharing the [URL here](https://affiliatenichebuilders.com/installing-ssl-certificate-on-easywp/).

![](https://asifrehan.com/wp-content/uploads/2020/02/SSL-padlock-icon-asifrehan-300x66.png)

Hope this post helps you find your way to get that padlock icon next to your own blog site as well!