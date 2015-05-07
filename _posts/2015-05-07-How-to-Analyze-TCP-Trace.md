---
layout: post
title:  How to analyze TCP trace
keywords: TCP, tcpdump, tcptrace
status: published 
---

I know so many posts have addressed this topic. However, in my perspective, none of them really give us a quick look of tools. So, the goal of this post is to give everyone an overlook of whole analysis procedures.

<!--more-->

## TCPDUMP

Tcpdump is a famous package analyzer. Many people might be familiar with a higher level tool such as [Wireshark](https://www.wireshark.org/) (Ethereal). However, I think tcpdump already provides almost everything we need for analyzing (cooperating with other tools).

Let's first take a look on the result from tcpdump. To use tcpdump, you simply type tcpdump in your command line.(You should have the root permission.)

	$ sudo tcpdump

This is output showing on the screen.
![]({{ site.baseurl }}/public/figures/tcpdump/tcpdump_trace.png)

Well, interpreting the output from tcpdump is not my goal, so I just skip this step and talk about on options. There are some options I usually use:

- Don’t resolve hostnames, ports, etc
^
	$ sudo tcpdump -n
	
- Print absolute sequence numbers
^
	$ sudo tcpdump -S
	
- Specify an interface, eg. eth0
^
	$ sudo tcpdump -i eth0
	
- Write to a file
^
	$ sudo tcpdump -w /path/to/file

- Onle capture a subnet network, eg. 192.168.1.0/24
^
	$ sudo tcpdump net 192.168.1.0/24
	
- Specify src, dst
^
	$ sudo tcpdump src 1.2.3.4
	$ sudo tcpdump dst 5.6.7.8

- Specify src, dst port
^
	$ sudo tcpdump src port 7439
	$ sudo tcpdump dst port 18000
	
### Example

Now, we combine them together. If I want to capture the subnet 192.168.1.0/24 and write to a capture_file, the command will be
	
	$ sudo tcpdump net 192.168.1.0/24 -w capture_file
	
(For more details, please check the [map page](http://www.tcpdump.org/tcpdump_man.html) of tcpdump.)






