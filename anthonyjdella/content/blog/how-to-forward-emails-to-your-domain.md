---
title: "How to Forward Emails to Your Domain 📧"
date: 2021-12-30T12:49:27+06:00
writtenDate: "December 30, 2021"
authors: "Anthony Dellavecchia"
featureImage: images/blog/gmail.png
postImage: images/blog/gmail.png
tags: ["domain", "how-to"]
---
### TLDR: Set up Gmail forwarding so it looks like your email address matches your domain name.

Want to organize your email inbox?

How about exposing a different email address for different purposes?

I set up email forwarding so that I can receive emails to my existing Gmail inboxes, but use different email address names.

For example, these are my different email addresses:

1. hello@anthonydellavecchia.com - general things
2. dev@anthonydellavecchia.com - software development
3. hireme@anthonydellavecchia.com - job seeking
4. photo@anthonydellavecchia.com - photography
5. design@anthonydellavecchia.com - design

### What's the Point?

Everything is 
* Organized
* Routed
* Exposed to the respective audience! 


### Use Cases

So, if I have a photography job, I can tell my client to email me at photo@anthonydellavecchia.com, or if I'm looking for a job, I can ask companies to email me at hireme@anthonydellavecchia.com. Then, those emails are nicely organized in Gmail.


## How to Set it Up

First thing is to have a domain with a domain registrar such as Namecheap, Google Domains, HostGator, GoDaddy, etc (I recommend Google Domains). This post won't go over instructions to set that up, so you may want to Google that first.

Next, you will want to enable Email Forwarding from your Domain registrar settings. I use Namecheap, so this image is from Namecheap, but a similar process will apply if you're using a different registrar.

![Image](/images/blog/forwarding.png)

After that, you will want to redirect emails from an Alias to an existing email address.

![Image](/images/blog/redirect.png)

As you can see, anthonyjdella.photo@gmail.com is an existing email address that I have with Gmail. I want emails sent to photo@anthonydellavecchia.com to be forwarded to anthonyjdella.photo@gmail.com.


Next, log into your existing Gmail account, in this example it's anthonyjdella.photo@gmail.com.

1. Go to Manage Google Account -> Security tab
2. Enable 2-Step Verification
3. Add an App Password

### Step 1
- Click on your google picture
- Click on `Manage Your Google Account`
- Click the `Security` tab
![Image](/images/blog/manage-google.png)

### Step 2
(Image not shown)
- Click on `2-Step Verification`
- Enable it and link it to your mobile phone
- This will enable the App Password setting on the previous page

### Step 3
- Click `App Passwords`
- Select `Mail` as the App
- Select `Other (custom name)` as the Device
- Enter your desired email address (i.e. photo@anthonydellavecchia.com) or the email which you want to expose
- This generates a one time password which you need to copy

![Image](/images/blog/app-password.png)

### Step 4
- Back in Gmail, go to your settings
- CLick the `Accounts and Import` tab
- For `Send mail as`, click `Add another email address`

![Image](/images/blog/gmail-settings.png)

### Step 5
- Enter the name of your new email address (i.e photo@anthonydellavecchia.com)
- Click `Next Step`

![Image](/images/blog/gmail-settings-2.png)

### Step 6
- Enter `smtp.gmail.com` for the SMTP Server
- Enter the current email address you're logged in as for `Username` (i.e anthonyjdella.photo@gmail.com)
- Enter the password which we copied earlier from `Step 3`

![Image](/images/blog/gmail-settings-3.png)

### Step 7
(Image not shown)
- A verification email will be sent to you so just verify it with the code Google sends you

### Step 8
- Back in settings select `Reoky from the same address the message was sent to`

![Image](/images/blog/gmail-settings.png)

---

#### Now your email alias is set up! You can add a filter and label in the next steps!

### Step 1
- Back in Gmail settings, click the Filters and `Blocked Addresses` tab
- `Create a new filter`
- In the `To` section add the new email address you created (i.e. photo@anthonydellavecchia.com)
- Click `Create filter`
- Apply a label and name it with same name as your email address
- `Also apply filter to X matching conversations`
- Create filter

![Image](/images/blog/gmail-settings-4.png)

#### Repeat these steps for other email addresses you want

Now, you have successfully routed emails to various email address and organized them! For more info, watch this [video](https://youtu.be/RbT28X0wiRw).

Thanks for reading!
