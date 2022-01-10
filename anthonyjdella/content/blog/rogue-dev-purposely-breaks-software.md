---
title: "Rogue Dev Purposely Breaks Software 🚫"
date: 2022-01-09T12:49:27+06:00
writtenDate: "January 9, 2022"
authors: "Anthony Dellavecchia"
featureImage: images/blog/corrupt.png
postImage: images/blog/corrupt.png
tags: ["security", "devops", "dependency"]
---

### TLDR: A software developer who made some highly used open source software, decided to go rogue and inject a bug into his software, making it usable. This affected every other dependency (and developer) using his software.

---

#### Bug Breaks my Software Deployment

Over the weekend, I was deploying some software (to Firebase) with CI/CD pipelines. But for some reason, the pipelines were failing. The failure occurred at this stage of my GitHub Actions workflow:

{{< highlight yml >}}
    - uses: FirebaseExtended/action-hosting-deploy@v0
    with:
        repoToken: '${{ secrets.GITHUB_TOKEN }}'
        firebaseServiceAccount: '${{ secrets.FIREBASE_SERVICE_ACCOUNT_ANTHONYDELLAVECCHIA }}'
        channelId: live
        projectId: anthonydellavecchia
        entryPoint: "./anthonyjdella"
{{< /highlight >}}

This is the visual representation of my failed pipeline:
![Image](/images/blog/cd-fail.png)

I then went over to the Firebase Extended [Github repo](https://github.com/FirebaseExtended/action-hosting-deploy) to see if anyone else was having similar issues. And yep, many others were experiencing the same issue:

![Image](/images/blog/issue.png)
*[(link)](https://github.com/FirebaseExtended/action-hosting-deploy/issues/188)*

---

#### Rogue Developer, Marak

Well, it turns out, `Action-hosting-deploy` was using a dependency called `colors`, created by [Marak](https://github.com/Marak) (the rogue developer), which is a tool that colors and styles your node.js console. This npm package gets over 20 million downloads per week, so its very popular! The dependency tree for this GitHub action looks something like this:

* Action-hosting-deploy
    * Firebase-tools
        * cli-table
            * colors (subdependancy which is causing the issue)
    * winston
        * logform
            * colors (subdependancy which is causing the issue)

So what? Well, `Marak`, the creator of `colors` (mentioned above) added some code into his project to purposely break it. **He added an infinite loop to purposely break his code!**

![Image](/images/blog/infinite-loop.png)

[(link to Marak's commit)](https://github.com/Marak/colors.js/commit/074a0f8ed0c31c35d13d28632bd8a049ff136fb6)

**This is very much intentional and not an accidental bug. It was malicious.**

---

#### Why is Breaking his own Software Bad?

You may be wondering why breaking his own software is bad? Well, Marak knows that his software is being used by other software. So if his breaks, so will theirs. Think of it as a chain reaction. If his breaks, other software that uses it will break too. Because of ["dependency hell"](https://en.wikipedia.org/wiki/Dependency_hell), this affects millions of developers.

#### Why Did Marak Do This?

Marak was upset that corporations were using his open-source software and not paying for it. It's basically that simple. He posted an [article on his blog](https://web.archive.org/web/20210628030444/https://marak.com/blog/2021-04-25-monetizing-open-source-is-problematic).

#### Who is Right?

Most developers are against Marak and his actions, however some are supportive. GitHub and NPM actually suspended his account for this. Some supporters argue that these corporations have no right, because it's his personal software. What do you think?

#### How Do You Fix It?

If your software was using `colors`, you would have to revert to the previous (non-broken) version. But because of this developer's outburst, you should definitely use another package instead. [Chalk](https://github.com/chalk/chalk) is another alternative that is recommended.

It's really important to have a dependency management system in place for your projects. Tools like [Snyk](https://snyk.io/), or [SonarQube](https://www.sonarqube.org/) will help you detect dependency issues so you can quickly resolve them.

#### Future Effects

This might have a big impact on Open Source Software (OSS) and software licensing. Marak's code was licensed with the infamous MIT license, so it's free for commercial use. In the future, will developers be more hesitant to use this license? For example, if you license your software as fair code, it is open source (so others can use it for free) but prevents commercial usage. This seems like the best of both worlds.

Some Fair Code Licenses include:

1. Commons Clause
2. Confluent Community License
3. Server Side Public License (SSPL)

**Will fair code replace Open Source?**

**For more information:**
- https://snyk.io/blog/open-source-maintainer-pulls-the-plug-on-npm-packages-colors-and-faker-now-what/
- https://www.bleepingcomputer.com/news/security/dev-corrupts-npm-libs-colors-and-faker-breaking-thousands-of-apps/


**Thanks for reading! 🙌**

**Please react or comment to this article, down below!**
