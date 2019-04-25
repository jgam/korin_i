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

