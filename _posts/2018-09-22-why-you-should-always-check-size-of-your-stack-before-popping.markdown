---
title: Why you should always check size of stack before popping
layout: post
date: '2018-09-22 01:05:00 +0530'
categories: competitive-programming
---

So I was solving problems related to Stacks data structure on HackerRank.
The mistake that I was doing was popping elements from Stack before even checking that if it already
has any element in it or not.

Problems like these leads to RunTime Errors while submitted solutions on online judges.

Here is the updated code ... Now in the method ```popAndCheck()``` I've implemented condition to check
whether the stack size is greater than 0.


<script src="https://gist.github.com/an0nh4x0r/7e86e593a8ff947f783d303597165d9e.js"></script>

{% include disqus.html %}