---
title: "What is database?"
layout: post
date: 2019-04-25
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- file
- Database
- system calls
- mySQL
category: blog
author: jgam
description: database
---

## Database?

Before going to school, I remember parents buying me a pencilcase with bunch of pencils in it. Because I only had a few pencils at that time, I could easily fit in more pencils as I grew up. However, when I entered middle school, the story was a little different. I had to get a new pencil case while having a box-like pencil container on my personal desk. Now, I don't recall how many pencils I have had nor the number of pencil cases that I changed. Similar to this, Computers wanted to store the data and first created a file to store the data. As more files come across, we needed a storage to store those files and found out the database.

In 1970, Edgar Frank Ted Kerd created relational database in IBM. The relational database is still used these days and had a few innovative functionalities involving searching, storing, and updating(basic CRUD) in both safer and faster ways. The popular relational database includes *MySQL, Oracle, SQL Server, PostgreSQL, DB2, ACCESS.* It is good that knowing one of those languages will allow a huge hand-on knowledges for relational database. Now we can use MySQL to see what the DB is like

## MySQL

Started by Oracle, MySQL grew rapidly with web as a web database. MySQL has similar structure as that of excel spread sheet. In the database, there exists lots of tables and these tables can be grouped as **schemas.** These schemas then get accumulated on **database server.**

Now, what is so special about MySQL? (It seems like this is no different from excel spread sheet.)

**Security** is a powerful functionality for the database. Authorization is also another functionality that allows which one to have permissions to CRUD whereas users can only READ the data. The basic user is **root** and this acts as a superuser who can do anything on mysql server.

Let's run mysql server through terminal!
1. cd /usr/local/mysql/bin/
2. ./mysql -uroot -p

Now, we are into mysql server!

## SQL(Structured Query Language)

It is a language that all the relational databases use to communicate with them. This makes the language very efficient because unlike other languages, knowing this will allow you to use other RDB without any problems. Now, let's make or create a table that includes some data.

```javascript
 create table topic(
    ->   id INT(11) not null AUTO_INCREMENT,
    ->   title VARCHAR(100) NOT NULL,
    ->   description TEXT NULL,
    ->   created DATETIME NOT NULL,
    ->   author VARCHAR(30) NULL,
    ->   profile VARCHAR(100)
    -> , PRIMARY KEY(id));
```

This simple SQL code creates a table called *topic* with these attributes. When it is successful, we can CRUD(create read update and delete)

### CREATE

insert into 'table_name' ('column_names') VALUES ('values for each column_names')

### READ

select * from 'table_name';
select id,title,created from topic where author='jgam' order by id DESC;

### UPDATE

update 'table_name' SET 'column_name' = 'value' WHERE id=2;
**Here, the id is very very integral unless otherwise, you will change every column_name set to a value.**

### DELETE

delete from 'table_name' WHERE id = 5;
**also it is very integral not to forget where here!**

## WHY RDB?

Now, we looked at the database but why do we need *Relational Database*?

Let's think about it this way.

## Internet and Database

Computers can be connected through internet and this is why internet is so called as an innovation. How does this work? One computer can send request and receive response from the other computer. For example, when we type wikipedia.com, we ask for a request to wekipedia.com's domain and the server on wikipedia's side sends respone back to the web server that initiated the request.

Here is the picture (webserver)

Here is the picture (client & server)

MySQL then installs two programs simultaneously: database client & database server. We can only access to database server through database client even if it seemed that we accessed database server directly. Then, where does that database client exist?

It was ./mysql command before we actually delat with database. Through this client, we were able to send database commands.
