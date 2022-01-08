---
title: "How to Check your Website Users (Minus Yourself)"
date: 2021-12-04T12:49:27+06:00
writtenDate: "December 4, 2021"
authors: "Anthony Dellavecchia"
featureImage: images/blog/googleanalytics.png
postImage: images/blog/googleanalytics.png
tags: ["analytics", "how-to"]
---

Google Analytics is a web analytics tool that lets you track & report your website's traffic. It shows you information such as how many users have visited your site, what devices they use (mobile or computer), how they found your site (direct url, link from other sites), etc.

Google Analytics, or similar type of analytics tool, is a must have for any front-end developer, as it helps them track user engagement.

I have enabled Google Analytics on this site since it's creation, but I noticed that most of the traffic/stats is coming from myself. I love this site, and go on it frequently (afterall, it is my product). But the problem with this, is that this isn't a good representation of my user engagement since, I probably visit the site more than most folks.

So, I wanted to find out how to exclude myself from Google Analytics, to get a true sense of my actual users.

The most useful resource I followed was from [here](https://www.optimizesmart.com/how-to-block-internal-traffic-in-ga4/).

There are two major steps:

1. Create a Data Filter

2. Define Internal Traffic

3. Enabling a Report that shows My Traffic

### Create a Data Filter

Basically, this activates an Internal Traffic filter or a Developer Traffic filter. I set mine up for internal traffic because its a little easier to set up. Developer traffic requires you to download a Chrome Extension. Instructions for each option is [here](https://support.google.com/analytics/answer/10108813).

### Define Internal Traffic

This assigns an IP address, or range of IP addresses to a property. That property is used in the Data Filter step from above.

### Enabling a Report that shows My Traffic

Then, you go into the Report view of Google Analytics and create a view for the traffic property that you defined.

Now, when you visit Google Analytics, you have 2 views. Your public facing traffic, and your developer traffic.

If you want more info, check out the link above.
