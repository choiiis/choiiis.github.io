---
title: "'no matching key exchange method found' ssh error Solution 해결 방법"
excerpt: "How to solve 'no matching key for diffie-hellman-group1-sha' ssh error"

categories:
  - Linux
tags:
  - [Linux]

permalink: /linux/no-matching-key-exchange-error-solved/

toc: true
toc_sticky: true
 
date: 2021-12-24
last_modified_at: 2021-12-24
published : false
---

Error Msg

Unable to negotiate with <IP> port <port no.> : no matching key exchange method found. Their offer: gss-group1-sha1-toWM5Slw5Ew8Mqkay+al2g==, diffie-hellman-group-exchange-sha1, diffie-hellman-group1-sha1

Solution

host <IP>
KexAlgorithms +diffie-hellman-group1-sha1