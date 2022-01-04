---
title: "Building This Site"
date: 2021-09-28T12:49:27+06:00
authors: "Anthony Dellavecchia"
featureImage: images/allpost/keyboard.jpg
postImage: images/allpost/keyboard.jpg
tags: ["build"]
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


### CI/CD Error Fix


##### STEP 1:
If you get the following CI/CD error:

```
Error: fatal: remote error: upload-pack: not our ref 9b3f2092d9959fe1406f9062c5a50a71293636c9

Error: fatal: Fetched in submodule path 'anthonyjdella/public', but it did not contain 9b3f2092d9959fe1406f9062c5a50a71293636c9. Direct fetching of that commit failed.

fatal: 
  Error: The process '/usr/bin/git' failed with exit code 128
```


##### STEP 2:
Go into anthonyjdella/ and run:

```
git submodule  update --init --recursive --remote
```


##### STEP 3:
cd public/ then
git status

Message will show that the HEAD is detached:
```
HEAD detached at 1b2926f
```

##### STEP 4:
Go back into anthonyjdella/ by
cd ..

Generate static files:

```
hugo -t portio
```

cd public/

##### STEP 5:
You'll see changes now. Then add and commit them.

```
git commit -m "....."
git branch my-temporary-work
git checkout master
git merge my-temporary-work
```
