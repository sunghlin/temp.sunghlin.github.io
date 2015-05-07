---
layout: post
title:  How to analyze TCP trace
keywords: TCP, tcpdump, tcptrace
quote: 
---

I know so many posts have addressed this topic. However, in my perspective, none of them really give us a quick look of tools. So, the goal of this post is to give everyone an overlook of whole analysis procedures.

<!--more-->

## TCPDUMP

Tcpdump is a famous package analyzer. Many people might be familiar with a higher level tool such as [Wireshark](https://www.wireshark.org/) (Ethereal). However, I think tcpdump already provides almost everything we need for analyzing (cooperating with other tools).

Let's first take a look on the result from tcpdump. To use tcpdump, you simply type tcpdump in your command line.(You should have the root permission.)

	$ sudo tcpdump

![](https://github.com/sunghlin/sunghlin.github.io/blob/master/public/figures/tcpdump/tcpdump_trace.png)