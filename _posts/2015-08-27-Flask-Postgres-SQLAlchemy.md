---
layout: post
title:  "Local Postgres & Flask"
date:   2015-08-27
---

### Postgres

If you already have Postgres installed on your development machine, whether it be local or virtual, skip a few lines to where I create the database.

OS X: Download/install/open [Postgres.app](http://postgresapp.com/). You should now have a running Postgres server with the benefit of an awesome elephant in your menubar. Then add the following line to your .bash_profile so you have command line tools `export PATH=$PATH:/Applications/Postgres.app/Contents/Versions/9.4/bin`.

Postgres will give you a default table with the same name as your username, or more technically speaking `$USER`. That's cool, but you should probably create a new one for your application. You can run the following code from your standard terminal prompt, without having to connect to Postgres.

`$ createdb your_database_name`

If you want to make sure it worked follow this sequence (note that I am using `$USER=#` as the prompt from Postgres):

* `$ psql`
* `$USER=# \list` and make sure your database is listed.
* `$USER=# \c your_database_name` if you'd like to make sure you can connect.

Now the address to that database is: `postgresql://localhost/your_database_name`.

### Using Flask

Even if you're using SQLAlchemy make sure you install psycopg2. SQLAlchemy is pretty smart, it'll recognize a Postgres database and promptly import psycopg2.

`$ pip install psycopg2`

Make sure you do that in your virutalenv if you've been using that for development. (If you don't know virutalenv and want to learn more check out [A Non-Magical Intro](http://www.dabapps.com/blog/introduction-to-pip-and-virtualenv-python/).)
