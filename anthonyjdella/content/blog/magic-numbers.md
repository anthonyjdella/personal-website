---
title: "Magic Numbers 🪄"
date: 2018-04-17T12:49:27+06:00
writtenDate: "April 17, 2018"
authors: "Anthony Dellavecchia"
featureImage: images/allpost/magic-numbers.jpg
postImage: images/single-blog/magic-number.png
tags: ["best-practices"]
---

### TLDR: A software development principle to follow with an example.

Today, I got feedback from a code review and learned something new. It was about ["magic numbers"](https://en.wikipedia.org/wiki/Magic_number_(programming)), which are unique values with unexplained meaning or multiple occurrences which could (preferably) be replaced with named constants.

I've known about the concept of using constants rather than hard-coding values, but I didn't think of that for "magic number" situations. It's a pretty simple concept but I just wanted to share what I learned.

### Magic Numbers are Bad

Magic numbers are language agnostic, but below, you'll see a code snippet in Java WITH magic numbers (the bad way).

{{< highlight java >}}class MagicNumber {

    String pipeDelimitedString = "This|is|an|example|of|Magic|Numbers|123 Parker Road|cityline@gmail.com";
    String [] splitString = pipeDelimitedString.split("\\|");

    obj.doSomething(splitString[7]);
    obj.doSomething(splitString[8]);           
} {{< /highlight >}}

As you can see, I am simply splitting a pipe delimited string that contains some useful data (Home Address and Email Address).

splitString[7] refers to the 8th element, or 123 Parker Road, which is a Home Address

splitString[8] refers to the 9th element, or cityline@gmail.com, which is an Email Address

### Why is that bad? We’ll it’s not easy to read.

splitString[n], where n is a number, may not mean anything from an outsider looking at your code. The numbers 7 & 8 have no meaning!

Now, you’ll see a code snippet in Java WITHOUT magic numbers (the good way).

{{< highlight java >}}class MagicNumber {
  
  String pipeDelimitedString = "This|is|an|example|of|Magic|Numbers|123 Parker Road|cityline@gmail.com";
  String [] splitString = pipeDelimitedString.split("\\|");
  
  obj.doSomething(splitString[Constants.HOME_ADDRESS]);
  obj.doSomething(splitString[Constants.EMAIL_ADDRESS]);           
}

class Constants {
  
  public static final int HOME_ADDRESS = 7;
  public static final int EMAIL_ADDRESS = 8;
} {{< /highlight >}}

I’ve created a constants class, with some constants (HOME_ADDRESS = 7 and EMAIL_ADDRESS = 8).

Constants.HOME_ADDRESS & Constants.EMAIL_ADDRESS are much easier to understand and now have meaning!

### If you aren’t convinced, what’s easier to read:
splitString[Constants.HOME_ADDRESS] or splitString[7]?

Again, this is just ONE example of magic numbers but there are many more. Thanks for reading!

