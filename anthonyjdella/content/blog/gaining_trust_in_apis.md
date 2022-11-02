---
title: "Gaining Trust in APIs and What to Look For"
date: 2022-11-02T12:00:27+06:00
writtenDate: "November 02, 2022"
authors: "Anthony Dellavecchia"
featureImage: images/blog/gaining-trust.png
postImage: images/blog/gaining-trust.png
tags: ["api", "security", "best-practices"]
---

> **TLDR:** Organizations are developing and consuming APIs at a rapid pace. So, how can organizations trust an API?

---

## Intro

API security is a huge topic and solving that problem is an even bigger challenge. Now quick disclaimer, there is no magic bullet when it comes to API trust. But there are some things you should take into account. Now this is just a start and there is only so much that I can cover in this article.

## API Growth and Challenges

APIs continue to grow at an exponential rate. According to Akamai, API hits are growing 30% year over year and are expected to reach 42 trillion hits by 2024. Furthermore, Gartner predicts that by 2025, 30% of third-party APIs will be used in applications, up from less than 10% in 2021.

With this growth, comes challenges, namely security challenges due to an increase in attack surface. If you're using unsecured APIs, that makes for an easy target for attacks. If you're using an API and it has an outage, well that part of your application is going to be down too.

To add fuel to the fire, according to Gartner, explosive growth will continue in APIs and that growth will surpass how teams will be able to manage them. According to Gartner, by 2025 less than 50% of enterprise APIs will be managed, as API growth surpasses management capabilities. So, not only are we having security challenges, but APIs are outgrowing their own support.

## Gaining Trust

So now that we understand how important APIs are, how fast they are growing, and on the flip side, how potentially vulnerable an API can be, how can we trust an API?

Well, before trust comes knowledge, "knowledge is power". I can't stress how important this is. If you're consuming an API, you first need to know what APIs you're using and what they do. That sounds really simple, but just think about it.

### Similar to a relationship

Trust in APIs is just like a trust in a relationship. You don’t go around, throwing your trust in every person you see, right? Otherwise you might end up with a broken heart, Or even worse, an empty wallet. Before you trust someone, you’ve got to know something about that person. You’ve got to understand them and know what they’re about. The same thing applies to an API. You’ve got to understand that API.

### Criticality of the data

Next, think about what data is being passed in and passed out of that API? Is it marketing data or sensitive customer data? Depending on that answer, a lot of things may change. And if you put the same amount of time and effort for all types of data, that wouldn't be productive.

If I’m filling up my car with gas, I don’t need to invest a lot of time in building trust in that gas pump. I mean I can trust that it’ll pump out gas. And if the pump doesn't work, it's not that big of a deal because this isn’t critical.

On the other hand, if I’m jumping out of a plane, I’m definitely going to need to have a lot of trust in the parachute before I jump. I’m going to be inspecting every inch of that parachute. Because jumping out of a plane is critical, it's life or death.
What I'm trying to say is that you should think about the data and pick and choose your battles to see if it's worth the time & effort to invest in. Because not all uses cases are equal.

### Don't over expose data

Are you exposing the right amount of data or an excess amount of data, more than what is required? 

If you're trying to sell shoes, why would you need my date of birth? Why would you need my medical history if I was buying a pair of glasses? I mean in the early days, companies were just trying to gather as much data as possible, but sometimes less is more.

Think about these simple but ever so important questions! Take some time to truly understand the data and the API. And trust will eventually come. Because whenever you consume an API you are inheriting it. Both the good and the bad.

### Understand the technology

Let's say for example, you are using Twilio's Programmable Messaging to send text messages with code. Well, what data should you being texting?

It might help to understand the technology of SMS itself. SMS is not end-to-end encrypted. SMS is just plain text, meaning the messages you send aren't secure.

Whenever you send a text, the contents of that message are actually stored by cell carriers. Furthermore, if you do something wrong, the authorities are able to monitor texts using surveillance systems. And guess what? If carriers and the authorities can get ahold of this, so can hackers.

Now, if you’re wondering how this works in the context of Twilio, we provide customers with message and phone number redaction, which makes it so that messages don’t retain any data after they’re transmitted. So if you’re a financial or healthcare company, you might want to turn this on.

Having this underlying understanding is necessary because knowing this would mean that you wouldn't send over credit card or social security info via SMS.

### Understand the context

Let me give you another example. Who has taken a COVID test and then had to wait for your results to be sent to you? Well how did you get your results?

Some of you might have gotten a phone call, others might have gotten an email, and some services even send you a text message. 

But guess what? Due to some HIPAA (Health Insurance Portability and Accountability Act) regulations, sending lab results over text is non-compliant. How could you work around this? Well, instead of directly sending a text with the lab results, you would instead send over a notification or a link to a secure portal that contains the results.

See, having some background knowledge is critical. If you didn't understand the what the API does, what data you're dealing with, or the tech itself, how can you expect to build or gain trust?

## Compliance to Gain Trust

After we’ve gained some knowledge about the APIs we’re consuming, what can we look at to gain trust? For one, we can look to see if they’re compliant. Now, this in itself does not guarantee that we can trust an API, it just reinforces that it follows a certain set of regulations. And it’s important to note that compliance does not equal security. With that said, looking at compliance is a decent start for building trust.

If you’re dealing with an API that collects data from residents throughout the EU, you’d better make sure that its GDPR (General Data Protection Regulation) compliant. If you’re not familiar with GDPR, it’s a regulation that came in effect in 2018, and it outlines expectations for handling user data within the EU.

If you’re dealing with an API that transfers credit card data, you’ll need to make sure its PCI DSS (Payment Card Industry Data Security Standards) compliant. If you’re not familiar with PCI DSS, it’s a standard that enterprises that handle any credit card information.

If you want to make sure an API follows international standards in information security, you’ll want them to be ISO/IEC 27001 compliant.

### Example with Twilio

There are lots of certifications of compliance that adhere to certain regulations. Let’s look at Twilio as an example. Twilio is certified under ISO/IEC 27001, has attestations to ISO/IEC 27017 and ISO/IEC 27018, and maintains SOC 2 compliance. On top of that, Twilio allows customers to enable FIPS (Federal Information Processing Standards) Level 3, a standard for cryptography. A Business Associate Addendum (BAA) to Twilio’s Terms of Service has been added so there is shared responsibility between Twilio and its customers when it comes to HIPAA (Health Insurance Portability and Accountability Act). Twilio Voice is PCI DSS Level 1 compliant, so we can collect credit card data over the phone and/or make payment on behalf of customer applications. We are a PCI Level 3 Merchant, so we can accept credit cards as a form of payment, but credit cards don’t enter our environment. We don’t separate EU customers from non-EU customers, and instead apply the high standards of GDPR to all users and all data, not just EU personal data.

Now, whenever you’re building trust with a person, it’s important that you communicate frequently and set some boundaries and expectations. Well, if you’re consuming an API, shouldn’t the same things apply? Frequent communication with your partnerships is important and so is being on the same page about expectations. You can do this by enforcing SLA’s and compliance. You should apply the same rigor to enforcing uptime, performance, security, licensing terms, and product roadmaps as you do for traditional SaaS services.

## Tips for Producing an API

This is great and so far we’ve been looking at things from a consumer perspective. Now, let’s look at the flip side, if you’re a company producing APIs. What you can do to gain customer trust?

First off, don’t just prioritize meeting compliance goals. Of course that is important, but also think about things from your customers perspective. Look at what your customer really needs and get things right. Of course, regulation is extremely important, just don’t stop there. You can’t think of compliance as a one-time checking a box activity. It’s ongoing and will continue to grow. 

At Twilio, we have a value “wear the customers’ shoes” and I think that all organizations dealing with compliance should adhere to as well. Do what is right for your customers.

### Get back to basics

Get back to the basics, enforce authorization by using a protocol like OAuth. Maintain an inventory of your APIs. Use a least privilege principle so each entity only has authorization to perform the minimum function required. Apply rate limiting to your API and limit the size of the payload.

### Handle data like it's radioactive

Now here are some tips for organizations that are handling personal data. Think of handling personal data like handling a radioactive material.

If you’ve got people moving it around all over the place, that increases the chance of them to leak that material. The same thing applies to personal data. Try not to move it around too much because you run the risk of data leaks.

Also, think about how you’re going to dispose of that radioactive material. You’re not just going to throw it away in a trash can, you need to dispose of it with care. The same goes for sensitive data.

Also, don’t just gather as much radioactive material as possible. Stockpiling that is a huge risk. The same goes for data. You shouldn’t just be collecting large amounts of data, only collect what you need.

Finally, you wouldn’t want any Jane or Joe handling that radioactive material, you need someone who is trained and experienced to handle it. The same applies to your organization. Have trained professionals working with that data. At Twilio, for example, all employees take annual security training.

## Conclusion

If you were looking for a magic bullet which allows you to instantly gain trust, sorry to disappoint you. There really is no one-size fits all answer to this. And even if you are able to gain trust, trust does not equal security. You should NOT inherently trust an API because of its name recognition or past history. You should always be cautious and on the lookout. Do your due diligence and follow a shift left mindset to security.

---

**Video**
- I presented this as a talk at API Days NYC on July 28, 2022. If you'd like to watch it, [here's the Youtube video](https://www.youtube.com/watch?v=elgcCqnNeEs).

---
