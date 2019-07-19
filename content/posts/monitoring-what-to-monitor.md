---
title: "Monitoring, What to Monitor"
date: 2019-07-12T10:41:45-07:00
draft: true
---
I seem to get this question a lot which tells me that there is still a lot of confusion about what to monitor, trend, and track for metrics. But it’s entirely understandable why there is confusion. We seem to have a proliferation of monitoring tools and with all their bells and whistles and it is easy to get lost in all the pretty graphs and charts. Most who ask the question are looking for a blueprint, but unfortunately it depends.
The guidance I give is to start with the golden signals, which was made popular in the Google book on “Site Reliability Engineering”. The 4 golden signals are Latency, Errors, Traffic, & Saturation (LETS). These signals provide the framework for defining what metrics and measures you need to track to effectively monitor a service. We’ll start with an example fake website with database to provide an example.

## Latency
The time it takes to service a request. In this category, we want to know how long a user request takes. Full round trip time is great, but also how long each component takes. There is the frontend application that serves users and also the backend application which is the database such as mysql. You’ll want to have a good understanding of how long it takes for users to get a response and which component is the bottleneck. Think about measuring from the furthest point out all the way in. Things to measure: latency from loadbalancer, web front end, database queries, round trip from a browser, and transactions to 3rd parties.

## Errors
Somewhat self-explanatory. Here we want to measure requests that failed, requests that returned the wrong results, and requests beyond our latency threshold. Besides the obvious transactions that are labeled as errors, we should also consider those transactions that are beyond any thresholds that we have set. If our website takes credit cards we should also record declines as a metric and alert on them if the number of declines exceeds our daily “normal” volume. This serves as an indication that there might be something else wrong. Typical errors to record are application flagged errors and metrics beyond our defined threshold.

## Traffic
A measure of how much demand is being placed on the system. For a website this is often recorded in hits and visitors. Measuring traffic will provide the data to determine when you need to scale in or out. It is also important to measure backend traffic as well and compare the two. What I mean by this is there should be some type of ratio between the number of hits on the front end with the number of database transactions. Also don’t forget to look at transactions with 3rd party systems you may be integrated with such as credit card. Some measure that are typically gathered, number of hits, number of visitors, number of signups, credit card transactions, credit card charge amounts, and number of database transactions. Don’t forget to look at different levels of time such as minute, hour, day, and day of week.

## Saturation
This is a measure of how full your service is. Saturation is typically a difficult metric to wrap our brains around because the metrics used to measure saturation are a bit vague. Take for example CPU. When a CPU reaches 100% does not necessarily mean that the system is overloaded. In the course an application execution the CPU will spike to 100%. For CPU to be useful the metric must be trended over time and averaged for a time period. So instead of instantaneous CPU, it would be better to measure CPU over 1, 5, and 15 minutes. Other measures for saturation include memory, load, disk i/o, diskspace, and network traffic. Obviously there is a lot more so its best to reason about the things that help determine whether you need to scale the service.

## Conclusion
As I mentioned earlier there is no blueprint on what we should be monitoring, trending, or obtaining metrics for. Every metric that is monitored should be actionable and add to the value of information. Monitoring signals that are not actionable just add to the noise and distract us from improving either the performance, reliability, or scalability of a system. LETS or the golden signals is a good framework used to determine what we should be monitoring within a service and hopefully answers the question of what we should actually monitor. 
