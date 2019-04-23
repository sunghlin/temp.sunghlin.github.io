---
layout: post
title:  Change the Timezone of Docker Container
keywords: Docker, timezone, container
status: published
---

Nvidia GPU Cloud (NGC) container is easy to use. However, I always got annoyed by the timezone inside the container, which shows UTC time. So, I did some researchs in the internet, and realized many people experience the same issue. Thus, I summerize what I have learned from this exercise.

<!--more-->

Many posts from the internet suggest to use `tzdata` (you have installed it in the container), and put the following commands inside Dockerfile. The commands here set it to Pacific time. For the name of other timezones, you can check [the list](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) from Wiki.

```
RUN sudo echo "America/Los_Angeles" > /etc/timezone
RUN sudo dpkg-reconfigure -f noninteractive tzdata
```

However, this mechanism assumes tzdata assumes that your system does not have setup `/etc/localtime`, and will read the config from `/etc/timezone`. If you like me, who might want to source from pre-build container, this trick might not work well because `tzdata` will also check `/etc/localtime` first. In my situation, NGC container always has its localtime set to UTC, so I cannot change the timezone successfully.

So, there are two solutions for this:

### (Option 1) Delete `/etc/localtime` first

```
RUN sudo /bin/rm -f /etc/localzone
RUN sudo echo "America/Los_Angeles" > /etc/timezone
RUN sudo dpkg-reconfigure -f noninteractive tzdata
```

### (Option 2) Modify `/etc/localtime` directly

```
RUN /bin/ln -fs /usr/share/zoneinfo/America/Los_Angeles /etc/localtime
RUN sudo dpkg-reconfigure -f noninteractive tzdata
```

If you set it correctly, you will see the following messages when you are building the container.

```
Current default time zone: 'America/Los_Angeles'
Local time is now:      XXXXXXX
Universal Time is now:  XXXXXXX
```
