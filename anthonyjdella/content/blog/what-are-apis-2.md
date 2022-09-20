---
title: "What are APIs (Part 2)?"
date: 2022-03-10T12:00:27+06:00
writtenDate: "March 10, 2022"
authors: "Anthony Dellavecchia"
featureImage: images/blog/what-are-apis-2.png
postImage: images/blog/what-are-apis-2.png
tags: ["api","back-end", "front-end"]
---

> **TLDR:** A bit more details about APIs ([part 1 here](https://anthonydellavecchia.com/blog/what-are-apis/)) using an easy-to-understand analogy.

---

## Recap

In my [previous article](https://anthonydellavecchia.com/blog/what-are-apis/), I explain what an API is (without any code). Let's recap what that article mentions.

* Think of an API as a customer ordering food at a restaruant
    * The customer makes a request (with their order) to a waiter
    * The waiter brings that request to the kitchen
    * The kitchen/chef makes the food
    * The waiter delivers the order back to a (happy) customer

I also broke this concept down into a few extra steps. Let's take a look at them again:

- Step 1: Recognize that you are hungry and would like some food.
- Step 2: Go to a restaurant that serves what you're looking for.
- Step 3: Browse the menu.
- Step 4: Decide what you would like to order.
- Step 5: Speak with a waiter and make your request.
- Step 6: Wait a little while, and eventually your waiter will bring you your order.

I'll talk about each of these in more detail, in the subsequent sections. And yes, I love using food 🍔 analogies because who doesn't like food?!

---

## Step 1: Recognize that you are hungry and would like some food 

Before you order food, you need to recognize that you are hungry and want to eat! I mean, who goes to a restaurant when they're not hungry?

In terms of APIs, that same principle applies. As a software developer, you need to recognize that you could use an API when you need it.

So how do you know when to use an API?

Unfortunately, there's no equivalent of your stomach growling in software development. But a good question to ask yourself is this: is what I'm trying to do, already available? If the answer is yes, you can bet that there's already an API for it.

---

## Step 2: Go to a restaurant that serves what you're looking for

Alright, now that you know you are hungry, you go to a restaurant to get some food. In the API world this means you pick a service that provides an API you'd want to use.

But before going to that restaurant, how do you choose a location? You might pull out local reviews to get a catalog of places you're interested in eating. If you're hungry for Italian food you might search for that. Or maybe Japanese food. You get the point.

For APIs, you might do a Google search or you could go on RapidAPI.com and look for an API that fits the category you're interested in. RapidAPI has categories that are grouped together, so for example, if you want an API for food it might be in the Food category.

---

## Step 3: Browse the menu

You've finally decided on a place to eat. Now it's time to look at the menu. Here is where you decide what you want and you do this by reading the descriptions of each dish.

With an API, you will look at API documentation which will describe how the API works and how to use it, similar to a menu. Reading this will help you decide what you need and how to use it.

---

## Step 4: Decide what you would like to order

You understand the menu and see the perfect dish. But your order is pretty big, you want a drink, an appetizer, an entree, and a dessert. Here you compile a list of what you want so you can get ready to give it to your waiter.

For APIs, you need to gather the necessary data needed for the API and then get ready to make a request to the API.

---

## Step 5: Speak with a waiter and make your request

A waiter helps you process your order by taking in your order request. This happens by you giving them your order, then them delivering it to the kitchen.

You make a request to the API by sending it some data. The API will deliver that request to their backend services.

---

## Step 6: Wait a little while, and eventually your waiter will bring you your order

After a certain amount of time, the waiter gets the food from the kitchen and delivers it to your table. You can finally eat!

After the response comes back from the backend service, it is delivered to your application as a response. So now you've gotten back what you requested!

---

So again, just think of an API as ordering food at a restaurant. I hope this was an easy analogy to understand!

**For more information:**
- [Part 1: What are APIs](https://roadmap.anthonydellavecchia.com/what-are-apis)

---
