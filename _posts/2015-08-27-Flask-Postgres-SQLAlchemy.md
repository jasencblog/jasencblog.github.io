---
layout: post
title:  "Flask, Postgres, and SQLAlchemy"
date:   2015-08-27
---

## Flask, Postgres, and SQLAlchemy

There are a lot of tutorials around the web that describe how to set these three things up. However, I found that most of them were vague or used incredibly simplistic examples that don't scale well. I tried a few different sources out, mixing and matching until I could get things to work. Then I slowly removed things one by one until things continued to work. Follow along with me if you'd like to avoid having to do that on your own.

### Local Environment

If you already have Postgres installed on your development machine, whether it be local or virtual, skip a few lines to where I create the database.

Since I am on a OS X (say what you will) I was able to use the [Postgres.app](http://postgresapp.com/) which was easy enough, just download, unzip, drag to your applications folder, and open the application. You now have a running Postgres server. And an awesome elephant in your menubar.

Add the following line .bash_profile so you have command line tools:

`export PATH=$PATH:/Applications/Postgres.app/Contents/Versions/9.4/bin`

Postgres will give you a default table with the same name as your username, or more technically speaking `$USER`. That's cool, but you should probably create a new one for your application. You can run the following code from your standard terminal prompt, without having to connect to Postgres.

`$ createdb your_database_name`

If you want to make sure it worked follow this sequence (not that I am using `$USER=#` as the prompt from Postgres):

* `$ psql`
* `$USER=# \list` and make sure your database is listed.
* `$USER=# \c your_database_name` if you'd like to make sure you can connect.

Now the address to that database is going to be:

`postgresql://localhost/your_database_name`

If you've been developing locally using SQLAlchemy but with a sqlite3 database, since it was most likely already on your computer, you just need to put that `postgresql://localhost/your_database_name` everywhere that you would normally reference your sqlite3 database. That's it, so from the Postgres.app documentation you ONLY follow the SQLAlchemy section but making sure you update your database URL EVERYWHERE:

* `database_setup.py`
* `if_you_have_a_database_populator.py`
* `models.py` or any other place your models might be stored.

Then make sure you install psycopg2 because although you don't need to include it anywhere in your application, SQLAlchemy is going to realize that it needs it and try importing it whether you have it installed or not. So:

`$ pip install psycopg2`

Make sure you do that in your virutalenv if you've been using that for development. (If you don't know virutalenv and want to learn more check out [A Non-Magical Intro](http://www.dabapps.com/blog/introduction-to-pip-and-virtualenv-python/).)

Then run the commands like you normally do and keep your fingers crossed (...also like you normally do):

* `python database_setup.py`
* `python if_you_have_a_database_populator.py`
* `python run_your_server.py`

Let's commit that stuff.


### So what now with Heroku?

Since this post is already getting lengthy I'm going to assume the following:

* You have [Git](http://git-scm.com/) on your computer.
* You have a [Heroku](https://www.heroku.com/) account, and your [SSH setup](https://devcenter.heroku.com/articles/keys).

From there you can follow the [Getting Started with Python on Heroku](https://devcenter.heroku.com/articles/getting-started-with-python#introduction) article. But I'll gladly hold your hand if your palms aren't too sweaty and you promise not to hurt me with a fear of death grip.

#### The Dirty Work

* Turn off debugging through Flask by changing the line in your config.py from this: `DEBUG = True` to this: `DEBUG = False`.
* `$ pip install gunicorn` in your working environment.
* `$ pip freeze > requirements.txt`
* `$ nano Procfile` if you're up for Vim or just `$ touch Procfile` if you're already holding on too tight and open it in your favorite text editor.
* Add this `web: gunicorn runserver:app --log-file=-` *VERY IMPORTANT: in this example runserver:app needs to be exactly whatever it is that you would typical `python runserver.py` with!!!* Save that extensionless file.

Alright let's slow things down a bit and play with Heroku. `$ heroku login`, if you did the things I mentioned at the top of this section you should see this:

```shell
Enter your Heroku credentials.  
Email: example@mydomain.com  
Password (typing will be hidden):  
Authentication successful.  
```

Otherwise, maybe [get started?](https://devcenter.heroku.com/articles/getting-started-with-python-o)

#### Testing Heroku locally

Ok, we're getting close - can't you feel it?! Let's make sure things still work locally but this time through Heroku.

`$ heroku local` 

Hopefully, and eventually, you'll have about five to six lines printed on your terminal, and no more. Head on over to the localhost that is printed out. Let's keep our toes crossed that when you get there you'll feel like: "achievement unlocked: Gunicorn is properly hosting".

Alright, deep breathes. Get that achievement unlocked and when you do, if you haven't commit in a long time lets type something like:

`$ git commit -am 'docs: configure and test Heroku local`

instead of something like:

![XKCD - Merge branch 'asdfasjkfdlas/alkdjf' into sdkjfls-final](https://imgs.xkcd.com/comics/git_commit.png)

and make sure you push that up to origin.

#### Heroku's Postgres

Do you have butterflies yet? I sure do.

`$ heroku create`

Wait for it...

`$ git push heroku master`

Wait for it...

`$ heroku ps:scale web=1`

Wait for it... make sure you get this:  
`Scaling dynos... done, now running web at 1:Free.`

Ok cool but don't open it yet or you'll be sad emoji. We need to configure a Postgres database. But first check if one exists:

`$ heroku addons | grep POSTGRES`

If you get nothing back then type this in:

`$ heroku addons:create heroku-postgresql:hobby-dev`

Head on over to the dashboard at Heroku's website. You should be able to find your application and see that there is a database in the add-ons section. Click the database, you'll be taken to a list of all of your databases, click the right one, then under connection settings show the URL and copy that bad boy.

Save it in every location that your localhost database was saved. Run your programs again:

* `python database_setup.py`
* `python if_you_have_a_database_populator.py`

Ok, let's check that Heroko local again. 

`$ heroku local` 

Ok cool, now start a production branch like so:

`$ git checkout -b production`

And go back and replace all of those database links one more time with `"DATABASE_URL"`.

Let's commit [keeping up with our style guide](https://udacity.github.io/git-styleguide/) and then go hydrate for a bit, maybe get some coldbrew started or something.

#### More Secret Stuff

This is getting to be a specific use case because I am using Google+ Oauth2 but you can skip ahead if this isn't applicable to you.

Head over to [Google's Developers Console](https://console.developers.google.com/) and generate a new secret ID for your app. Download the new JSON but leave it be for a minute. Copy that client secret while you're still in there and head back over to Heroku. Go to your app again but this time go to settings. The second area down should be Config Vars. Click show, oh look there is that `DATABASE_URL` I mentioned. Click edit. Past your client secret as a value and give it a name, like `G_CLIENT_SECRET`. Make sure you save.

Ok, now put that JSON back in your app folder, but this time replace the value of "cient_secret" with `"G_CLIENT_SECRET"`.

Run this:

`$ heroku config`

And if you did it right you should see your database and client secret, the same as you saw it from the Heroku website.

Now we need to make another commit to Heroku, this one is a little trickier:


 