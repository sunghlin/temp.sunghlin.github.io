---
layout: page
title: About Me
permalink: /about/
---

I completed my PhD from [Quantitative Evaluation & Design Research Group](http://qed.usc.edu/) in Computer Science at University of Southern California in 2017. I received my B.S. degree in Computer Sience and Information Engineering at National Taiwan University in 2006, and M.S. degree from [Communication and Multimedia Laboratory](http://cmlab.csie.ntu.edu.tw/) in Computer Science and Information Engineering at National Taiwan University in 2008.

I am interested in Computer Networking, especially Distributed Systems and P2P Networks, Performance Modelling and Analysis, Economics and Game Theory, and Cloud Computing.

## Work Experience
- _Performance Analyst_, __NetApp__, Oct 2017 - Present
- _Teaching Assistant_, __CSci 402 Operating Systems__, Fall 2012 - Summer 2017
- _Intern_, __Teradata Labs__, June 2014 - Aug 2014
- _Intern_, __Fuji Xerox Palo Alto (FXPAL) Laboratory__, May 2013 - August 2013
- _Research Assistant (Adviser: Prof. Cheng-Fu Chou)_, __Communications and Multimedia Laboratory, Department of Computer Science and Information Engineering, National Taiwan University__, October 2009 - July 2010
- _Research Assistant (Adviser: Prof. Zhao-Ming Gao)_, __Department of Foreign Languages and Literatures, National Taiwan University__, September 2006 - September 2007

## Project Experiment

### Distributed System

#### Improve the performance of SQL-MR Execution Engine - Teradata Labs Intern
I profiled the performance of SQL-MapReduce Execution Engine and re-designed the mechanism to reduce the data transmission and I/O time between user defined functions and databases. 
1. Aggregating the output: Instead of sending result row by row in the original design, I caches rows and send it once to reduce the I/O time. This improves the performance by at least 20%. 
2. Eager sending: Sending cached data immediately if it is available. This improves the performance by 10%. 

#### MediaWall Framework - FXPAL Intern
I designed and developed media wall framework which instantiates and controls virtual machines to enable diversified screen presentations that are not limited by pre-installed projectors. Since this system works in a network, I built a centralized system to manage network resources and handle interactions between remote machines and services to enhance the performance. Moreover, I developed APIs to provide programmatic access from web-enabled platforms. To provide access interface, I programmed Web-based Graphical User Interfaces to enable presenters to manage projected screens on walls

#### Speed up loading large data sets to a Facebook-like system on Cassandra
Built Cassandra clusters with small-scale OpenStack virtual machines suitable for Facebook-like social network. Designed mechanisms equally distributing the workload to all running virtual machines. Coded multi-thread systems to handle different kinds of inputs without leaving the system idle.

### Networking

#### Performance Analysis for the Speed-Sensitive Channel Assignment
Developed and simulated probability models to correctly analyse the performance of channel assignment with rapid cell phone hand-offs. Explored the effect of adopting random walk or human walk to probability models for assigning channels.

### Peer-to-Peer

#### Implemented a distributed large-scale Digital Signage system.
Implemented a distributed large-scale Digital Signage system. Developed partial storage systems for video contents and advertisements by combining Content Distribution Network and Peer-to-Peer technologies

#### Implemented a real P2P IPTV system
Coded P2P Internet Protocol Television(IPTV) systems supporting channel browsing in Windows systems. Explored and measured effect of parameter settings for different network capability environments.

#### Exploit File Similarity in Peer-to-Peer Networks
Explored probability of having the same chunks among files in eMule file-sharing environments. Developed sharing mechanism capable of using similar chunks to speed up peer-to-peer file downloading.