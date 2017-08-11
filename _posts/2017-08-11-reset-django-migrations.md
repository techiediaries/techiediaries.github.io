---
title: Resetting Django Migrations
date: 2017-08-06 00:00:00 Z
tags:
- django
layout: blog
summary: How to effectively reset Django Migrations
image: "/images/blog/blogging-again.png"
---

Sometimes you'll need to reset your Django migrations or simply make a clean up .This process can be performed 
very easily in many situations but can also become complex if you have a big number of migration files and database
tables .In this tutorial I'll show you a few options to enable you to effectively delete or reset your Django database migrations 
without affecting the working of your project .

<h2>Case 1 : Dropping the whole database is not a problem </h2>

In this case we'll describe how to rest database migrations in a situation where you don't actually have a problem 
deleting or dropping your whole database .

<h3>Deleting migration files </h3> 

Start by deleting each migration file inside your project apps except for the Python module file __init__.py 

You can use a bash script in Unix based operating systems to do this quickly .

    find . -path "*/migrations/*.py" -not -name "__init__.py" -delete
    find . -path "*/migrations/*.pyc"  -delete   

The first line looks for Python files (migration files) inside migrations folder in each project's app except for 
__init__.py then delete them .

The second line looks for the Python compiled version of the previous migration files and delete them .

<h3>Dropping the database</h3> 

The next step would be deleting the actual database depending on the used database system 

For Sqlite ,you just need to delete the sqlite file which exists in your current folder and has an extension of 
.sqlite3 

If you are using MySQL you first need to connect to your MySQL server using your command line 

    mysql -u USERNAME -p PASSWORD 

Or 

    mysql -u root -p 

Then enter your password when MySQL prompts your for a password .

Next drop the MySQL database and create it again :

    drop database YOUR_DATABASE_NAME;
    create database YOUR_DATABASE_NAME;

If you want to confirm if the database has been deleted before re-creating it again use the show command 

    show databases;

For PostgreSQL you need to use psql utility .So first connect to your PostgreSQL database  using 

    psql DBNAME USERNAME       

psql will prompt you for a password ,enter it and type Enter .

Now you can drop your database with 

    DROP DATABASE dbname;

Then create it again 

    CREATE DATABASE dbname;


<h3>Re-creating migrations </h3>

The last step is to create your initial database migrations and migrate your database just like when you are starting a new Django project .

First generate initial migrations with :

    python manage.py makemigrations

Then invoke migrate command to create the database structure 

    python manage.py migrate


That's all you need to do in the case when dropping the whole database is not a problem which is only an option 
when you are just starting working on your project .

But that's not always the case ,sometimes you can't just delete a whole database ,maybe you need data for testing purposes on 
development phase or when you are on a production environment .How can you reset your migrations without affecting 
your actual database ?

<h2>Case 2 : Dropping the database is not an option </h2>

In this case we want to reset migrations but we don't want to drop the database .

<h3>Clear or roll back database migrations </h3>

First start by clearing and rolling back migrations without touching the actual migration tables .

    python manage.py migrate --fake appName zero

You need to replace appName with the actual app name and to do that for ach app you have in your project .

This command will un-apply all migration files for the specified app .

You can use showmigrations command to see all available migrations and to keep track of what you have cleared .  

    python manage.py showmigrations



<h3>Remove migration files </h3>

After faking the migrations for all apps we need to delete the migrations files inside migrations folder in each 
app .

You can use the previous bash script to automate this process in Unix bases OSs .

    find . -path "*/migrations/*.py" -not -name "__init__.py" -delete
    find . -path "*/migrations/*.pyc"  -delete

This will delete Python source files and also compiled Python files for migrations except for the special Python 
file __init__.py 

<h3> Make migrations again </h3>

Now you need to re-create the initial database migrations with the usual commands 

    python manage.py makemigrations

Next you need to migrate your database again but since your database already exist ,we didn't delete them ,remember ?!
with just need to fake the initial migrations using 

    python manage.py migrate --fake-initial

If you run migrate without --fake or --fake-initial you are going to get this error :

    django.db.utils.OperationalError: (1050, "Table TABLE_NAME already exists") 

So make sure to add the --fake-initial command switch .

Adding --fake switch marks migrations as run without actually running them .       

PS :

Before following any process described above it's advisable that you make sure you have no un-applied migrations 
before your proceed by running 

    python manage.py makemigrations 

You should get a message like this 

    No changes detected   

Otherwise apply the un-applied migrations first .

That's all I sincerely hope this is working for you as many developers are still finding problems reseting 
their database migrations especially if they can't drop the database But just make sure to follow the steps 
above and drop a comment if you have any problems .

Thanks for reading !



