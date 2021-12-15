---
title: JSON Resume
date: 2021-10-20T12:49:27.000+06:00
thumbnail: ../images/portfolio/firebase.png
service: API, Javascript, Firebase, CI/CD
client: Myself
shortDescription: I reversed engineered the JSON Resume Registry project so that it works on my privately hosted Firebase domain.
challenge: JSON Resume uses their own domain (e.g. http://registry.jsonresume.org/anthonyjdella). In order to use it, you have to use their own 'jsonresume' domain. 
solution: I didn't want to have to use their domain, so I reverse engineered their project to host it on resume.anthonydellavecchia.com

---

[JSON Resume](https://jsonresume.org/) is an open source project to standardize JSON-based resumes. JSON is a widely used file format that most developers are familiar with, so this is a great tool for developers. With this initiative, put your resume into a JSON file and it can be used with various front-ends. One resume with multiple themes!

http://registry.jsonresume.org is the webpage used for that project. If you append your GitHub username to that URL (e.g. http://registry.jsonresume.org/anthonyjdella) it will use GitHub APIs to search for that GitHub user and look for a file called `resume.json` under their public Gists.

You can then append a theme to the URL (e.g. https://registry.jsonresume.org/anthonyjdella?theme=spartan) to view it in multiple themes.

However, there are some issues with this project.

1. You have to use their JSON schema, which is not really customizable.
2. The included themes often times don't work or look less than stellar.
3. If I want to use it, I have to go to their domain (`registry.jsonresume`).

I really like this project but wanted to fix the above issues, so I reverse engineered it to: 

1. Use my personalized and customized JSON schema.
2. Include personalized themes to fit my design preferences.
3. Use my own domain (`resume.anthonydellavecchia`).

With this project, you can now visit https://resume.anthonydellavecchia.com and append a GitHub username to the end, as well as some themes.

Some of the themes I've customized include:

* "@anthonyjdella/jsonresume-theme-anthonyjdella-actual": "^1.0.6",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-caffeine": "^1.0.4",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-dave": "^1.0.0",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-elegant": "^1.0.9",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-github": "^1.0.3",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-kards": "^1.0.0",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-mocha-responsive": "^1.0.1",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-orbit": "^1.0.0",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-rocketspacer": "^1.0.0",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-simple-red": "^1.0.0",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-spartan": "^1.0.0",
* "@anthonyjdella/jsonresume-theme-anthonyjdella-stackoverflow": "^1.0.0"

(These are all deployed as NPM packages, so you can easily install them with `npm install`)

![Firebase](/images/portfolio/firebase-db.png)
This is the Firebase database used for this project. Anytime you append a GitHub username to the URL, that data will be added to this database and stored (for speed).

![Firebase](/images/portfolio/firebase-functions.png)
This is the Firebase Function (called registry) that is an API call triggered by an HTTP request. 

![Firebase](/images/portfolio/firebase-functions-2.png)
You can view the health of the API in this view.

![Firebase](/images/portfolio/firebase-hosting.png)
By default, Firebase will give you a domain with the projectname-firebaseapp.com. Since I didn't want to use this domain, I connected to to my personal domain in this view. You can also add subdomains which is pretty cool. Since I already own the domain `anthonydellavecchia`, I can redirect this project to `resume.anthonydellavecchia`.


View the source code here: [@customized-registry-functions](https://github.com/anthonyjdella/customized-registry-functions)
