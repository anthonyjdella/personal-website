---
title: "What are APIs?"
date: 2022-02-09T12:00:27+06:00
writtenDate: "February 09, 2022"
authors: "Anthony Dellavecchia"
featureImage: images/blog/what-are-apis.png
postImage: images/blog/what-are-apis.png
tags: ["api","back-end", "front-end"]
---

> **TLDR:** APIs are when software talks to each other. One software sends a request, another software sends back what they asked for.

---

## Why should you care about APIs?

As a developer (or even business) APIs help you save time, and makes your software development process much easier. This enables you to quickly create and release products. If these benefits sound interesting to you, please continue reading!

---

## What are APIs?

Before going into any technical details, let's look at a real-world example to give us some context. We will look at an interaction that everyone has experienced, ordering food at a restaurant.

Think about this situation for a moment. How would you normally order food?

In its simplest form, you would: make an order, then get your food shortly after (hopefully). In other words, you make a **request, then get back a response** (in the form of food). This basic type of interaction (i.e. making some sort of request, then getting some type of response back) applies to many other contexts. But for now, let's focus on the food ordering example.

Let's visualize this interaction below:

![Image](/images/blog/order-food.gif)

So, what does ordering food have to do with APIs?

At its core, APIs behave in the same way. Think of an API as a way for a piece of software to request information from another **piece of software, then receiving a response back**. Well, what kind of information are we talking about? For the most part, we are talking about data. Any data that some software wants. For example, a website might want to know the weather in a specific location. Or a social media app might want to know what people are up to. Basically, any data that meets your business needs.

Let's visualize how an API behaves:

![Image](/images/blog/api.gif)

As you can see, an API helps you request then receive data.

In the case of our food ordering example, a customer makes a request, which is then sent to the kitchen. The kitchen then processes the order and sends the food back to the customer. The customer doesn't need to know how the kitchen makes their food, just that they receive it and is the order that they asked for.

APIs work the same way. A system makes a request, which is processed by the receiver. The receiver then sends the response back to the requester. The requester doesn't need to know how the receiver processes the request, just that they receive the response and is the request that they asked for.

Now that we have an idea of what an API is, what does it stand for?

**A**pplication

**P**rogramming

**I**nterface

If you look at those three words, one of them might be less clear than the others. I'd bet that "interface" is that word. So, what does it mean?

Let's look at another example. If you want to listen to sounds from your computer, you have to plug headphones into your computer. But how do you do this? You'd plug the headphones into a port. The port, in this example, is an interface between your headphones and the computer. This port exposes functionality to the user, so the user gets what they want (sound). The user doesn't need to understand how this works, just that they get sound.

Interfaces in software act in the same principle. In the context of software, an Application Programming Interface helps software get information from other software without needing to know how it works, just that they get what they want.

![Image](/images/blog/port.png)

Do you see how this principle may be beneficial? Since your software just requests and receives what it's looking for, you save time by re-using functionality that already exists. There is no need to re-invent the wheel. Here's an example: why make homemade bread when you can just buy it from a store? Doing so would save you so much time, which helps you ship your product faster.

Great! Now that we have a better understanding of APIs, let's go into just a bit more detail. I'll go back to our earliest example: ordering food. As you know, there are a few extra steps that you need to take before ordering food. It's not quite as simple as just ordering, then receiving food. These steps can be broken down as follows:

- Step 1: Recognize that you are hungry and would like some food.
- Step 2: Go to a restaurant that serves what you're looking for.
- Step 3: Browse the menu.
- Step 4: Decide what you would like to order.
- Step 5: Speak with a waiter and make your request.
- Step 6: Wait a little while, and eventually your waiter will bring you your order.

Let's translate each of these steps in the context of APIs:

- Step 1: Recognize that you have data needs and would like to get it without having to build it from scratch.
- Step 2: Do an Internet search to find the API you're looking for.
- Step 3: Browse the API documentation.
- Step 4: Decide what data you need and how you would request it.
- Step 5: Interact with the API and send your request.
- Step 6: Wait a little while, and eventually your API will bring you your data.

I'll provide more details about each of these steps in a future article, but for now, just understanding what an API is should be enough to get you started.

---

## Where can you find an API?

Sometimes, finding the dish you want to order can be difficult. For example, if you want to eat pasta, you could either visit the restaurant that you've previously visited, or you might want to look online for a new restaurant with good reviews. Other times, you might not even know what you want to eat.

This idea also applies to APIs. If you want to use an API, you could either use one that you're familiar with, or you could do a Google search to find what you're looking for. But this can be difficult because there are so many APIs out there. And a lot of times, it can be hard to find the right API that you need. Sometimes, you might just want to browse APIs by categories and see what's out there.

Well, what if you wanted to make things easier? You might go to a buffet since you know they have all types of food. And what if you could visit an aggregate marketplace for all kinds of APIs? Wouldn't that be so much easier?

Thankfully, there's a product that does just this! RapidAPI is a marketplace/aggregate of APIs, to help you find the right API for your needs. You can think of it as a buffet of APIs because it's got every possible thing you might need.


---

## Want to Learn more?

This was just an introduction to help beginners understand APIs and why they are important. In a future article, I will go into more detail. I'll explain how you can find the right API for your needs, and how to use them (with code snippets). I hope this helped you! If you liked it, please follow me for more content like this.

---

**For more information:**
- [Original Article with Animations](https://roadmap.anthonydellavecchia.com/what-are-apis)

---
