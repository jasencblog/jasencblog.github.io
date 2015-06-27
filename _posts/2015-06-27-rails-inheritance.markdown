---
layout: post
title:  "Rails Inheritance & ActiveRecord::Base"
date:   2015-06-27
---

Ok, so yesterday I had a bit of fun while partaking in my slight Rails detour for the moment - that's why I said Eloquent JavaScript was going to be in a bit. I've found that I need to understand the basics of everything and start understanding the big picture as opposed to getting to a certain point with one technology to deem yourself certified to move on. Learn all the things.

So I was working on building a contact form in Rails and for some reason after I set up the database, migrated it, set up the controller and model, raked routes, and popped the server up I was getting an error about no methods. What I'm pretty sure is the problem is that my Contact class in my model wasn't properly inheriting the column names from my database. I couldn't figure it out, all of my files said the right things, so I added a few methods to Contact manually. I was able to preview the site but knew something would be wrong still.

I ran the rails console and ran Contact.new, and this was where I was able to define the problem, it returned:
{% highlight bash %}<Conact id: nil> {% endhighlight %}
but still didn't have the other methods that it should have gained from my database columns, like this:
{% highlight bash %}<Contact id: nil, name: nil, email: nil, comments: nil, created_at: nil, updated_at: nil> {% endhighlight %}
I started trouble shooting this but after an hour or so on top of the time I spent messing around with it in the morning just to be able to see if I could get the page to load, I decided it was time for the nuclear option.

I had created a new branch luckily when I started this work on the contact form. Deleted the branch. Ah so fresh so clean. NOPE. Database still contained the table that I originally set up, which I learned after migrating again. So how do I drop a table? Turns out really easily... include:
{% highlight bash %}drop_table :contacts{% endhighlight %}
in your code prior to creating the new one.

So that this:

{% highlight ruby linenos%}
class CreateContacts < ActiveRecord::Migration
  def change
    create_table :contacts do |t|
      t.string :name
      t.string :email
      t.text :comments
      t.timestamps
    end
  end
end
{% endhighlight %}

becomes this:

{% highlight ruby linenos %}
class CreateContacts < ActiveRecord::Migration
  def change
    drop_table :contacts
    create_table :contacts do |t|
      t.string :name
      t.string :email
      t.text :comments
      t.timestamps
    end
  end
end
{% endhighlight %}

Everything else went smoothly afterwards as I quickly copied the code back in (saved locally). And it was a success. Much faster to just redo a few files and commands than spend all day troubleshooting it. I mean I wish I knew what the problem was so I could avoid it in the future, but one day I'll connect the dots.

Made sure to delete that
{% highlight bash %}drop_table :contacts{% endhighlight %}
out of my migration file. Not sure if it would offer a new feature later, like every time I
{% highlight bash %}$ git push origin master{% endhighlight %}
my databse resets or something.
