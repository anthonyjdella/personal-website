---
title: Automated Job Search
date: 2018-03-21T12:49:27.000+06:00
thumbnail: ../images/portfolio/job-search.png
service: Nodejs, Automation, Web Scraping
client: Job Seekers
shortDescription: This script does automated web scraping on various websites to look for available job postings.
challenge: I want to be notified about newly posted jobs for select companies and roles. However, there is no notification system available.
solution: This script automatically searches for desired job postings and sends an email alerting me about those positions.

---
I wanted to be alerted of new job postings, so I created this script. The source code can be found on [GitHub](https://github.com/anthonyjdella/automated-job-web-scraping) and an article/blog post with instructions on how to build it is found [here](https://anthonyjdella.github.io/blog/how-to-never-miss-out-on-a-job-opening/).

In summary, it uses Puppeteer, an Automation library that automatically controls Chrome, to visit job seeking websites. Then, it scrapes that data, formats it, and sends those job postings to me via email.
