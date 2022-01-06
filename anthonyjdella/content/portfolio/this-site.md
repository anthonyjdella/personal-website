---
title: This Website
date: 2021-09-27T12:49:27.000+06:00
featureImage: images/portfolio/this-site.png
service: Web Development, UX Design
client: Myself
shortDescription: This website was built by myself with the help of Hugo, Portio theme, Firebase, and GitHub Pages.
challenge: I don't have a personal brand which displays my work, thoughts, skills, and experience.
solution: Create a simple website that showcases my professional skills.
tags: ["front-end", "webdev", "design"]

---

Initially, the goal of this site was to quickly create and deploy a personal website. However, over time, I became more and more invested in it. I've spend HOURS customizing and adding in new features. Check out [this Kanban board](https://github.com/users/anthonyjdella/projects/6) which shows how many enhancements I've made.

Since my main goal was to *quickly* create a website, I used [Hugo](https://gohugo.io/), a popular open-source static site generator. Hugo is built with Go lang. I decided to pick it just because of its popularity, speed, and available themes. To quickly make this site, I used a pre-built theme called [Portio](https://github.com/StaticMania/portio-hugo), however I wanted to customize it. And customize it is what I did! Since the start of this project, I've added a ton of customizations on top of the original theme. For example, I added a dark-mode theme, added a cool slide out menu, added multiple CSS animations, and much more! 

You can see my [forked project](https://github.com/anthonyjdella/portio-hugo) which I used as a Git submodule to my [source code](https://github.com/anthonyjdella/personal-website). I also created a [seperate repository](https://github.com/anthonyjdella/anthonyjdella.github.io) to house only the generated static files and deploy the site using [GitHub Pages](https://pages.github.com/). I also set up [Github Actions](https://github.com/features/actions) to deploy my code to a hosting platform, [Firebase](https://firebase.google.com/).

I don't do a lot of front-end work at my current job, so this project has helped me brush up on those skills. This website is ever growing and I intent to maintain it for some time. I will continue adding [new features](https://github.com/users/anthonyjdella/projects/6), blog posts, personal projects, and more! 

#### Design

* [Source code](https://github.com/anthonyjdella/personal-website)

* [Source code for Theme](https://github.com/anthonyjdella/portio-hugo)

* [Static site code](https://github.com/anthonyjdella/anthonyjdella.github.io)

#### Deploy

{{< highlight yml >}}

name: Deploy to Firebase Hosting on merge
'on':
  push:
    branches:
      - master
jobs:
  build_and_deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true
      - run: |
          echo 'Deploying to Firebase...'
          cd anthonyjdella
      - uses: FirebaseExtended/action-hosting-deploy@v0
        with:
          repoToken: '${{ secrets.GITHUB_TOKEN }}'
          firebaseServiceAccount: '${{ secrets.FIREBASE_SERVICE_ACCOUNT_ANTHONYDELLAVECCHIA }}'
          channelId: live
          projectId: anthonydellavecchia
          entryPoint: "./anthonyjdella"

{{< /highlight >}}

#### Build

As shown above, there are three code repositories. The Source code for Theme & Static site code are submodules of the source code.

* After making changes, start the server locally with `hugo serve`.

* After viewing changes, build the static files using `hugo` or `hugo -t portio`.

* Push changes in `public/` to the static site code repository to deploy the site.

* Push changes in `themes/portio` to the source code for theme to make changes to the theme.

* GitHub Actions picks up the changes and deploys the site to Firebase, where it is hosted (using a custom domain name).