---
title: Daily Sit-Down
date: 2023-01-26T12:49:27.000+06:00
writtenDate: "January 26, 2023"
authors: "Anthony Dellavecchia"
featureImage: images/portfolio/daily-sit-down.gif
service: REST API, Airtable, Twilio Studio
client: Developers
shortDescription: I built a Daily Stand-Up replacement. Try it out by texting (844) 668-2535
challenge: Daily Stand-Up sucks. You have to do it at a scheduled time, you have to stand up, and you have to listen to "Chad" ramble for 15 minutes
solution: This app makes Daily Stand-Up asynchronous, you can do it sitting down, and you don't have to listen to "Chad" anymore
tags: ["twilio", "low-code", "airtable", "python", "flask", "api"]

---

[Daily Stand-Up](https://www.atlassian.com/agile/scrum/standups) is a meeting that many developers have to do on a daily basis. And it SUCKS!

The reasons why we (developers) hate it:

1. It's just another meeting
2. You have to stand up
3. You have to listen to that one rambling co-worker (aka Chad)

I built this app that solves these problems

---

It was built with:
 - [Studio](https://www.twilio.com/docs/studio), a low-code tool from Twilio
 - [Airtable](https://airtable.com/), a database/spreadsheet
 - REST APIs that I built in Python and Flask

If you want to try it out, text anything to **(844) 668-2535**

---

Here's how it works:
1. You can set a scheduler that will text you at a given time
2. When you reply, it checks to see if your number is valid (it does a number match from a database)
3. Through code, it identifies your name
4. It asks you: what did you do yesterday, what will you do today, do you have any impediments?
5. After you respond, it sends the data to Airtable and stores it in the database
6. You get a link to the Airtable, so you can see your team's updates

Check out the code [here](https://github.com/anthonyjdella/level-up-with-twilio-studio)

---

By the way, I presented this to ~600 RSVPs during a 1-hour Twilio Webinar

Register [here](https://interactive.twilio.com/level-up-with-studio-prototype-enhance-and-share-your-workflows-webinar) to view the free recording

![Image](/images/portfolio/level-up.png)
