---
title: This Website
date: 2021-09-27T12:49:27.000+06:00
thumbnail: images/portfolio/this-site.png
service: Web Development, UX Design
client: Myself
shortDescription: This website was built by myself with the help of Hugo, Portio theme, Firebase, and GitHub Pages.
challenge: I don't have a personal brand which displays my work, thoughts, skills, and experience.
solution: Create a simple website that showcases my professional skills.

---
This site is created with [Hugo](https://gohugo.io/), a popular open-source static site generator. Hugo is built with Go lang. I wanted to create this site quickly, so I used a pre-built theme called [Portio](https://github.com/StaticMania/portio-hugo), however I did want to customize it. Therefore, I [forked that project](https://github.com/anthonyjdella/portio-hugo) and used it as a Git submodule to my [source code](https://github.com/anthonyjdella/personal-website). I also created a [seperate repository](https://github.com/anthonyjdella/anthonyjdella.github.io) to house only the generated static files and deploy the site using [GitHub Pages](https://pages.github.com/). I also set up [Github Actions](https://github.com/features/actions) to deploy my code to a hosting platform, [Firebase](https://firebase.google.com/).

#### Design

-- Source code

-- Source code for Theme

-- Static site code

#### Build

As shown above, there are three code repositories. The Source code for Theme & Static site code are submodules of the source code.

After making changes, start the server locally with `hugo serve`.

After viewing changes, build the static files using `hugo` or `hugo -t portio`.

Push changes in `/public` to the static site code repository to deploy the site.

Push changes in `/themes/portio` to the source code for theme to make changes to the theme.

GitHub Actions picks up the changes and deploys the site to Firebase, where it is hosted (using a custom domain name).