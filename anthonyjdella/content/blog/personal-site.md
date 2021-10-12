---
title: "How to Build This Site"
date: 2021-09-28T12:49:27+06:00
featureImage: images/allpost/keyboard.jpg
postImage: images/allpost/keyboard.jpg
---

This is for my reference, so I remember how to make changes to this site without any hiccups. 

1. ```cd into personal-website directory```
2. Make changes.
3. ``` hugo serve``` to start local server.
4. Commit and push changes to personal-website repository (source files).
5. If changes are done to the Portio theme, ```cd into themes/portio ```.
    1. Commit and push changes to portio-theme repository (theme files).
6. ``` hugo -t portio``` to build static files which will go in the `/public ` directory.
7. ```cd into public directory```
8. Commit and push changes to anthonyjdella.github.io repository (static files).
9. GitHub pages will automatically deploy to `anthonyjdella.github.io`.
10. GitHub Actions will pick up changes made to the master branch and deploy to `anthonydellavecchia.com`, which is hosted on Firebase.