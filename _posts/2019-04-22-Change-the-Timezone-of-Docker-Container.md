---
layout: post
title:  Change the Timezone of Docker Container
keywords: Docker, timezone, container
status: draft
---

Nvidia GPU Cloud (NGC) container is easy to use. However, I always got annoyed by the timezone inside the container, which shows UTC time. So, I did some researchs in the internet, and realized many people experience the same issue. However, the most common solution does not do the trick to me. After playing with Dockerfile for a while, I finally found the solution to my environment. 

<!--more-->

## My environment: 
OS: Ubuntu 18.04

Docker: 18.06.1-ce

## The popular solution (Not work in my environment)

Many posts have suggested to use `tzdata` (you have installed it in the container), and put the following commands inside Dockerfile. The commands here set it to Pacific time. For the name of other timezones, you can check [the list](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) from Wiki.

```
RUN sudo echo "America/Los_Angeles" > /etc/timezone
RUN sudo dpkg-reconfigure -f noninteractive tzdata
```

This mechanism assumes tzdata will read the config from `/etc/timezone`
