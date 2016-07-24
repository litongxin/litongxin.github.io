---
layout: post
title: "MongoDB, son of a biscuit"
description: "MongoDB is an open-source document database, and the leading NoSQL database."
---

Why I want to complain about MongoDB?  

#### Installation  
  If you think only run `brew install mongodb`, you are totally wrong.  
  The **biscuit** thing is setting up dbpath for it. It took me almost 20 mins to make it work and start mongodb's server!!!  
{% highlight bash %}
sudo mkdir -p /data/db  
sudo chmod 0755 /data/db
sudo chown {userName}:staff /data/db  
{% endhighlight%}

#### Log tracker  
  Using mongojs for nodejs and mongodb integration, the mongojs module is easy to use for CRUD operations.  
  The **biscuit** thing is that mongodb server log cheat me!!! When I insert one message for one collection first time, the logger print out. Then I insert some, it shows nothing. So I am trying to figure out why I can't insert successfully. It tooks me 1 hour to check my code and google the reason.  
  Finally, I run `db.{collection_name}.findOne(key:value)` and `db.{collection_name}.find()`, all message are saved without any logger!!! T.T

#### Basic Usage
Start mongdb server: `mongod`  
Access mongdb using console: `mongo`  
Get basic command: `help`

#### Intergrate with nodejs
[MongoJS](https://github.com/mafintosh/mongojs) is a brilliant little Node.js package that lets you access MongoDB using an API that is extremely similar to MongoDB's JavaScript shell.

Add mongojs dependency into package.json file, run `npm install mongojs`.  
Add mongdb configuration into app.js file like following:
{% highlight bash %}
var mongojs = require('mongojs');
var databaseUrl = "mydb";
var collections = ["users"]; // Collections is a set (array) of collections our application uses
var db = mongojs.connect(databaseUrl, collections);
db.runCommand("mongo"); //Trigger the mongdb server log to make sure connect successfully!!!
{% endhighlight%}
Then `db.users.find/save/update/delete` to implement CURD Operations.
