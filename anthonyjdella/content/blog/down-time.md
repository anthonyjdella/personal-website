---
title: "Is 99% Good?"
date: 2022-01-04T12:49:27+06:00
writtenDate: "January 4, 2022"
authors: "Anthony Dellavecchia"
featureImage: images/blog/downtime-logo-black.png
postImage: images/blog/downtime-logo-black.png
tags: ["devops", "resiliency"]
---

If you ever took a test at school, you'd probably be really happy with getting a 99 grade. After all, it's almost a perfect score.

But when you're talking about software systems, is 99% availability good?

Well, if your system needs to be available 24/7 everyday, **99% won't cut it**.

### Downtime Table

Take a look at the below table. It shows how much downtime (in time) equals a given percentage.

| Availability &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|    Annual Downtime     |
| ------ | ----------- |
| 99%   | 3 days, 15 hours, 40 minutes |
| 99.9% | 8 hours, 46 minutes |
| 99.99%    | 52 minutes, 36 seconds |
| 99.999%    | 5.26 minutes |
|  &nbsp;  |  &nbsp; |
### What's this Mean?

If your system should be available at all times, a 99% availability means that your system can have almost 4 days of downtime per year! For a system that needs to be available, that is a terribly long time.

Imagine if you have a business critical system that fails. If it was down for almost 4 days, your company could lose millions/billions of dollars! Take for example, when [Facebook was down in 2021](https://en.wikipedia.org/wiki/2021_Facebook_outage) for about 7 hours. Their stock dropped 5%, or $40 billion dollars! This was only for a 7 hour outage. Can you imagine if they had just 99% availability and Facebook was down for 4 days?

### What should you aim for?

This depends on your system, and usually a probability or downtime measurement (rather than percentage) should be given. "Five 9's" is a common "standard" that systems try to aim for. **That is 99.999% availability (hence five 9s)**. Standards is in quotes because it really isn't a standard, it's just what's commonly mentioned in the industry as a goal to achieve.

Check out this [Wikipedia article](https://en.wikipedia.org/wiki/High_availability) for more information. 

Thanks for reading!
Please react or comment to this article, down below!
