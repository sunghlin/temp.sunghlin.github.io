---
layout: post
title:  How to analyze TCP trace
keywords: TCP, tcpdump, tcptrace
status: published 
---

I know so many posts have addressed this topic. However, in my perspective, none of them really give us a quick look of tools. So, the goal of this post is to give everyone an overlook of whole analysis procedures.

Coverage:

- Tcpdump - grab packets
- Tcptrace - analyze TCP packets
- Xplot.org - illustrate packet behaviors

<!--more-->

## TCPDUMP

Tcpdump is a famous package analyzer. Many people might be familiar with a higher level tool such as [Wireshark](https://www.wireshark.org/) (Ethereal). However, I think tcpdump already provides almost everything we need for analyzing (cooperating with other tools).

Let's first take a look on the result from tcpdump. To use tcpdump, you simply type tcpdump in your command line.(You should have the root permission.)

```bash
$ sudo tcpdump
```

This is output showing on the screen.
![]({{ site.url }}/assets/tcpdump/tcpdump_trace.png)

Well, interpreting the output from tcpdump is not my goal, so I just skip this step and talk about options. There are some options I usually use:

- Don’t resolve hostnames, ports, etc
```
	$ sudo tcpdump -n
```
- Print absolute sequence numbers
^
	$ sudo tcpdump -S
	
- Specify an interface, eg. eth0
^
	$ sudo tcpdump -i eth0
	
- Write to a file
^
	$ sudo tcpdump -w /path/to/file

- Only capture a sub network, eg. 192.168.1.0/24
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

## TCPTRACE

After we have the log, we are ready to analyze the trace. Tcptrace allows us to summarize and visualize the data. There are some options I usually use:

- Observe the summary of all link pairs

	$ tcptrace capture_file

This is output showing on the screen.
![]({{ site.url }}/assets/tcpdump/tcptrace_links.png)

- Show the detail of all links shown above

	$ tcptrace -l capture_file
	
- Only show the detail of the link No.4 (use -o with the link number)

	$ tcptrace -l -o4 capture_file

This is output showing on the screen.
![]({{ site.url }}/assets/tcpdump/tcptrace_link_4.png)

Tcptrace can also help us to convert those trace to visual figures. However, it can only generate the plot file. We have to use Xplot.org (will introduced later) to view it. There are five kinds of figures: Time Sequence Graph (-S), Throughput Graph (-T), RTT Graph (-R), Outstanding Data Graph (-N), and Segment Size Graph (-F).

- Draw the Time Sequence Graph (replace -S with others to plot other figures)
^
	$ tcptrace -S capture_file

- To draw all figures for link No.4
^
	$ tcptrace -G -o4 capture_file

(For more details, please check the [manual](http://www.tcptrace.org/tcptrace-manual/manual/node11_tf.html) of tcptrace.)

## Xplot.org

Xplot.org is an extended version for original Xplot, which was released in the late 1980s. Xplot.org supports color and more format. So, when you type the command, make sure you type xplot.org exactly. The output files from tcptrace drawing are XPL files. So, if I want to draw the figures about Time Sequence Graph for Link No.4 (, which is specified as g -> h in the above figure), I can type

	$ xplot.org g2h_tsg.xpl

This is output figure.
![]({{ site.url }}/assets/tcpdump/tcptrace_tsg.png)

(To read the figure, please check the [manual](http://www.tcptrace.org/tcptrace-manual/manual/index.html) of tcptrace.)
