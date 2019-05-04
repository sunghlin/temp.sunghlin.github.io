---
layout: page
title: About Me
permalink: /about/
---

I completed my Ph.D. from [Quantitative Evaluation & Design (QED) Research Group](http://qed.usc.edu/) in Computer Science at University of Southern California (USC) in 2017. I received my B.S. degree in Computer Sience and Information Engineering (CSIE) at National Taiwan University (NTU) in 2006, and M.S. degree from [Communication and Multimedia Laboratory (CMLab)](http://cmlab.csie.ntu.edu.tw/) in Computer Science and Information Engineering (CSIE) at National Taiwan University (NTU) in 2008.

I am interested in Computer Networking, especially Distributed Systems and P2P Networks, Performance Modeling and Analysis, Machine Learning, and Cloud Computing.

## Work Experience
- _Performance Analyst_, __NetApp__, Oct 2017 - Present
- _Teaching Assistant_, __CSci 402 Operating Systems__, Fall 2012 - Summer 2017
- _Intern_, __Teradata Labs__, June 2014 - Aug 2014
- _Intern_, __Fuji Xerox Palo Alto (FXPAL) Laboratory__, May 2013 - August 2013
- _Research Assistant (Adviser: Prof. Cheng-Fu Chou)_, __Communications and Multimedia Laboratory (CMLab), Department of Computer Science and Information Engineering, National Taiwan University__, October 2009 - July 2010
- _Research Assistant (Adviser: Prof. Zhao-Ming Gao)_, __Department of Foreign Languages and Literatures, National Taiwan University__, September 2006 - September 2007

## Project Experience

### Large-Scale Machine Learning

#### Large-scale Deep Learning in Shared Clusters <span class="default-span place-usc">USC - Research</span> <span class="default-span place-netapp">NetApp</span>

<span class="cite">Paper is published in IEEE MASCOTS 2018, with title __A Model-based Approach to Streamlining Distributed Training for Asynchronous SGD__</span>

We address two important problems for the application of this strategy to large-scale clusters and multiple, heterogeneous jobs. 
1. We propose and validate a queueing model to estimate the throughput of a training job as a function of the number of nodes assigned to the job; this model targets asynchronous Stochastic Gradient Descent (SGD), and requires only data from quick, two-node profiling. 
2. Throughput estimations are then used to explore several classes of scheduling heuristics to reduce response time in a scenario where heterogeneous jobs are continuously submitted to a large-scale cluster. These scheduling algorithms dynamically select which jobs to run and how many nodes to assign to each job, based on different trade-offs between service time reduction and efficiency (e.g., speedup per additional node). Heuristics are evaluated through extensive simulations of realistic DNN workloads, also investigating the effects of early termination, a common scenario for DNN training jobs.

### Cloud Computing

#### Resource Sharing for the Small Cloud

<span class="default-span place-usc">USC - Research</span>

<span class="cite">**Paper is published in IEEE ICDCS 2017, with title __Performance Driven Resource Sharing Markets for the Small Cloud__**</span>

Approximated an exponential growth stochastic model via TransientAnalysis to estimate the number of virtual machines exchanged within the cloud federation; developed market-basedgame-theoretic model that converges to efficient virtual machine sharing decisions at market equilibrium

### Distributed System

#### Improve the performance of SQL-MR Execution Engine

<span class="default-span place-teradata">Teradata - Intern</span>

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

#### Hybrid P2P Video Streaming

*(Paper is published in IEEE/ACM IWQoS 2015, with title __Sustaining Ad-Driven P2P Streaming Ecosystems A Market-Based Approach__, following up a journal in IEEE Transactions on Multimedia with a title __On Market-Driven Hybrid-P2P Video Streaming__)*

Re-designed sharing mechanisms to eliminate the problem of video playback pausesby up to 80% while providing sufficiently high quality of videos to peers; developed market-based game-theoretic modelthat uses advertisements as an incentive to satisfy all the market stakeholders.

#### Implemented a distributed large-scale Digital Signage system.
Implemented a distributed large-scale Digital Signage system. Developed partial storage systems for video contents and advertisements by combining Content Distribution Network and Peer-to-Peer technologies

#### Implemented a real P2P IPTV system
Coded P2P Internet Protocol Television(IPTV) systems supporting channel browsing in Windows systems. Explored and measured effect of parameter settings for different network capability environments.

#### Exploit File Similarity in Peer-to-Peer Networks
Explored probability of having the same chunks among files in eMule file-sharing environments. Developed sharing mechanism capable of using similar chunks to speed up peer-to-peer file downloading.
