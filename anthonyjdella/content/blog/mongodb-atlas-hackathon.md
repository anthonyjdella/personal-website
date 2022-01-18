---
title: "MongoDB Atlas Hackathon"
date: 2022-01-17T12:00:27+06:00
writtenDate: "January 17, 2022"
authors: "Anthony Dellavecchia"
featureImage: images/blog/atlas.png
postImage: images/blog/atlas.png
tags: ["mongodb", "database", "nosql", "python", "django", "back-end", "hackathon"]
---

> **TLDR:** I participated in a MongoDB Hackathon and share what I learned about MongoDB and Django.

---

## Hackathon

On Dev Community, I saw a post for a [Hackathon sponsored by MongoDB](https://dev.to/devteam/announcing-the-mongodb-at) and thought I'd give it a shot. I have no experience with MongoDB so I thought it'd be fun. Unfortunately, I saw the post only a few days before the due date, so I didn't have enough time to finish it. But I still learned a lot!

I picked the Time Series, category because I wanted to work with time series data, basically a collection of data in different time intervals. Think about a stock tracker or climate tracking. Time series data has some sort of final variable (unchanging) alongside data that frequently changes. For stock tracking the unchanged variable is the stock symbol (i.e. AAPL) and the data that changes frequently is the stock price.

Since I was using MongoDB for the first time, I also thought it'd be fun to use Django, a web framework in Python, for the first time. 

---

## My Idea

I looked for publicly available data and found an animal tracker, so I thought it'd be fun to track Bat movements and plot it on Google Maps. 

[Movebank](https://www.movebank.org/cms/movebank-main), is a public database, where scientists track animal movements by attaching a GPS device to the animal. Based on a certain frequencies, that data is recorded by the device and stored in the database.

There is a public API which gets this data, so developers can use it in various projects.

My idea for this was to:

1. Get European free-tailed bat tracking data from Movebank's API.
2. Store that data in MongoDB.
3. Convert it to Time Series data.
4. Display that data on a Map to track their movement history.

Unfortunately, I saw this Hackathon only a few days before the due date and did not have enough time to complete my idea. But I submitted it as is.

What I completed:

- ✅  Get European free-trailed bat tracking data from Movebank's API
- ✅  Store that data in MongoDB.
- ⛔ Convert it to Time Series data.
- ⛔ Display that data on a Map to track their movement history.

I plan on finishing this project later on, follow me for more on that.

---

## Sharing What I Learned

Although I didn't complete my idea, I still learned a lot and wanted to share that info.

### Virtual Environments in Python

Before installing Django, its good to understand `venv`, a virtual environment for Python. `venv` is a self-contained directory that has the Python installation plus external packages. Think of it as any other virtual environment. They should **NOT** be committed to your repo (you can put it outside the directory or just add it to `.gitignore`)!

Create a `venv` with:

{{< highlight shell >}}
python3 -m venv name-of-virtual-env-directory
{{< /highlight >}}

This will create the `name-of-virtual-env-directory` as well as the Python installation and any packages your project needs.

A best practice for handling virtual environments is to store them all in the same place. So, you might want to store them in your home directory or wherever your Git repos are stored. i.e.:

{{< highlight shell >}}
python3 -m venv ~/.virtualenvs/project-virtual-env
{{< /highlight >}}

After that, you can activate the virtual environment with:

{{< highlight shell >}}
source ~./virtualenvs/project-virtual-env/bin/activate
{{< /highlight >}}

Anytime you install a package with `pip`, it will be installed in the active virtual environment you're in. 

{{< highlight shell >}}
pip list
{{< /highlight >}}

Gives a list of all the installed packages within the **venv**.

After installing dependencies into the virtual environment, make sure to deactivate it when you're done. Use command:

{{< highlight shell >}}
deactivate
{{< /highlight >}}

`pip freeze` is similar to `pip list`, but it also give specific version numbers. Copy the contents of that list into a `reqirements.txt` file (which is committed into version control AKA Git). Then, when a user clones your project, they run the following, to install all of the project dependencies.

{{< highlight shell >}}
pip install -r requirements.txt
{{< /highlight >}}

Think of `requirements.tx` as `package.json` used in NPM.

| Another option: **virtualenv** is an even more popular option than **venv**. Look into using it [here](https://pypi.org/project/virtualenv/).


### MongoDB

MongoDB is a NoSQL, non-relational, schema-less, document-based database. Document-based means that the data is stored in key-value pairs, think about JSON. Check out the table below for a comparison between SQL and NoSQL.

|    Topic   |    SQL    |    NoSQL     |
|------ | ------ | ----------- |
| Type |  Table based databases   | Document based, like key-value pairs |
| Schema |  Uses a schema   | No need for a schema |
| Scaling |  Not preferred (vertical) | Preferred for scaling (horizontal) |
| ACID |  Best for [ACID properties](https://www.geeksforgeeks.org/acid-properties-in-dbms/)  | Not ACID compliant |
| &nbsp; |  &nbsp; |

![Image](/images/blog/sql-vs-mongo.png)
> This shows how you need to create a schema with relational databases, and how it's not needed in MongoDB.


### Django

MongoDB isn't officially supported by Django, a popular web framework with Python. PostresSQL, MySQL, Oracle, and SQLite are. But it is possible to do this per the [MongoDB docs](https://www.mongodb.com/compatibility/mongodb-and-django). This is because, usually, you'll want to use a relational database with Django. 

Flask is another popular web framework in Python. It's a better choice to use with NoSql databases. You can also use [django-nonrel](https://github.com/django-nonrel/mongodb-engine), which is a community fork to add NoSQL support to Django. However, it is not supported and uses an old Django version.

There are 3 options to connect to MongoDB with Django. **Pymongo, MongoEngine, and Djongo**. But by using **PyMongo**, a driver, you can connect MongoDB and Django. Instructions for this are in the subsequent section.

After activating the virtual env (from above), installing [Django](https://docs.djangoproject.com/en/4.0/topics/install/#installing-official-release) can be done with:

{{< highlight shell >}}
python -m install Django
{{< /highlight >}}

View the Django version with:

{{< highlight shell >}}
python -m django --version
{{< /highlight >}}

`cd` into a directory and enter the command to create a project:

{{< highlight shell >}}
django-admin startproject name-of-project
{{< /highlight >}}

To start the server & application:

{{< highlight shell >}}
python manage.py runserver
{{< /highlight >}}

Earlier, we created a project named `name-of-project`. We can also create apps within the project. Projects can have multiple apps (think of apps as modules). Use this command:

{{< highlight shell >}}
python manage.py startapp name-of-app
{{< /highlight >}}


| Directory |    Summary     |
| ------ | ----------- |
| name-of-project   | The root directory (can be named anything) |
| &nbsp;&nbsp;» manage.py | CLI utility |
| &nbsp;&nbsp;» name-of-project    | Directory for the Python package (e.g. name-of-project.settings) |
| &nbsp;&nbsp;&nbsp;&nbsp;» __init__.py    | Tells Python this directory is a package |
| &nbsp;&nbsp;&nbsp;&nbsp;» settings.py  |  Settings for Django |
| &nbsp;&nbsp;&nbsp;&nbsp;» urls.py  |  Table of contents and URL routing |
| &nbsp;&nbsp;&nbsp;&nbsp;» asgi.py  |  Entry-point for ASGI web servers |
| &nbsp;&nbsp;&nbsp;&nbsp;» wsgi.py  |  Entry-point for WSGI web servers |
| &nbsp; |  &nbsp; |


### PyMongo

According to [MongoDB docs](https://www.mongodb.com/compatibility/mongodb-and-django), **Pymongo** is the preferred way to use MongoDB with Django. But as mentioned above, there are some other options using **MongoEngine** and **Djongo**.

Install **PyMongo** with:

{{< highlight shell >}}
python3 -m pip install pymongo
{{< /highlight >}}

For installation with MongoDB, it might be good to install some optional dependencies with:

{{< highlight shell >}}
pip install pymongo[snappy,gssapi,srv,tls]
{{< /highlight >}}

As well as this (for using mongodb+srv://):

{{< highlight shell >}}
pip install dnspython
{{< /highlight >}}

There's a couple of ways to connect to our database session. One of which involves creating a `utils.py` file in the PROJECT folder (where `manage.py` is). 

{{< highlight shell >}}
from pymongo import MongoClient

def get_db_handle(db_name, host, port, username, password):

 client = MongoClient(host=host,
                      port=int(port),
                      username=username,
                      password=password
                     )
    db_handle = client['db_name']
 return db_handle, client
{{< /highlight >}}
> Use env variables to hide the username and password from being exposed. That's out of scope of this tutorial, but if you have questions, just ask.

Then, in the `app` directory, find `views.py`. From here, the function `get_db_handle()` can be accessed. 

Now, our MongoDB client is connected! If you'd like to check out how to set this up with MongoEngine or Djongo, just check out this [tutorial](https://www.mongodb.com/compatibility/mongodb-and-django).

---

**For more information:**
- [Virtual Environments in Python using venv](https://docs.python.org/3/tutorial/venv.html)
- [Virtual Environments in Python using virtualenv](https://pypi.org/project/virtualenv/)
- [Installing Django](https://docs.djangoproject.com/en/4.0/topics/install/#installing-official-release)
- [Django Tutorial 1-7](https://docs.djangoproject.com/en/4.0/intro/tutorial01/)
- [Django Design Philosophies](https://docs.djangoproject.com/en/4.0/misc/design-philosophies/)
- [PyMongo Docs](https://pymongo.readthedocs.io/en/stable/)
- [MongoEngine Docs](http://mongoengine.org/)

---
