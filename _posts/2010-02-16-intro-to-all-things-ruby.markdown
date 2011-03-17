---
published: false
layout: post
title: Intro To All Things Ruby
---

### What to install for Ruby

Might want to update your system first:

	sudo apt-get update
	sudo apt-get dist-upgrade

If errors, you might need to define your locale:

	sudo locale-gen en_US.UTF-8
	sudo /usr/sbin/update-locale LANG=en_US.UTF-8

You might have installed this before, but these you will need:

	sudo apt-get install build-essential
	sudo apt-get install ruby ri rdoc mysql-server libmysql-ruby ruby1.8-dev irb1.8 libdbd-mysql-perl libdbi-perl libmysql-ruby1.8 libmysqlclient15off libnet-daemon-perl libplrpc-perl libreadline-ruby1.8 libruby1.8 mysql-client-5.1 mysql-common mysql-server-5.1 rdoc1.8 ri1.8 ruby1.8 irb libopenssl-ruby libopenssl-ruby1.8 libhtml-template-perl mysql-server-core-5.1 libmysqlclient16 libreadline5 psmisc

Install RubyGems (like CPAN I guess):

	wget http://rubyforge.org/frs/download.php/60718/rubygems-1.3.5.tgz
	tar xvzf rubygems-1.3.5.tgz
	cd rubygems-1.3.5
	sudo ruby setup.rb

_Above from [Hackido](http://www.hackido.com/2009/11/install-ruby-on-rails-on-ubuntu-karmic.html)_


### Ruby Overview

[20 minute tutorial](http://www.ruby-lang.org/en/documentation/quickstart/) (uses IRB - interactive ruby shell) and a self-paced [tutorial](http://ruby-doc.org/docs/Tutorial/).

Key points to understand:

* Everything, I mean **everything** is an object... thus:
	- 20.class => Fixnum
	- Fixnum.class => Class
* More should go here probably :)

Download the source for the [Ruby Cookbook](http://www.crummy.com/writing/RubyCookbook/downloads/Ruby%20Cookbook%20Source.zip) or check out the open source mother of all [cookbooks](http://pleac.sourceforge.net/pleac_ruby/).

The "Bible" - aka [Pickaxe book](http://ruby-doc.org/docs/ProgrammingRuby/) (for older version of Ruby, but still a reference).

More books:

* [Humble Little Ruby Book](http://www.humblelittlerubybook.com/)
* [Book of Ruby](http://www.sapphiresteel.com/IMG/zip/book-of-ruby.zip)
* [Little Book of Ruby](http://www.sapphiresteel.com/The-Little-Book-Of-Ruby)

You can use the ri command to lookup Ruby Classes:

	ri String
	ri String#split


### Install Sinatra

	sudo gem install sinatra

To test create a new file called hello.rb and put this in it:

{% highlight ruby %}
	get '/' do
		"Hello World!"
	end
{% endhighlight %}

Then start the built-in web server by typing: *ruby hello.rb* and open http://localhost:4567 to view!


### Setup Github

You don't have to do this, but Git is pretty much the defacto version control system in Ruby world. This will allow us to share code real easily!

* [Create a free account](https://github.com/signup/free)
* [Setup SSH keys](http://help.github.com/linux-key-setup/)
* [Setting user name, email, token](http://help.github.com/git-email-settings/)
* [My GitHub page](http://github.com/kale)

With github (more generally git), you can do things like this:

	git clone git://github.com/kale/sharepoint_share.git local-folder

This will copy my SharePoint Share project to your local folder. Another cool feature of github is sharing "[gists](http://gist.github.com/)", basically snippets of code.

### Install Git

So while you don't have to use Github, I think you will want to at least use it locally. Well... you probably don't have to either, but you will have to figure out how to make heroku work with SVN.

	sudo apt-get install git-core
	sudo apt-get install git-gui (I haven't installed this... probably not needed!)

Then inside your project folder:

	git init => This will create an empty repository
	git add . => This will add ALL the files to the newly created repository
	git commit -a -m "Initial import" => This will commit changes

That is the basics. More commands:

	git log
	git status
	git diff

_Above taken from [xkoder](http://blog.xkoder.com/2008/08/13/git-tutorial-starting-with-git-using-just-10-commands/)_

Some other useful tips/sites:

* [Ignoring files](http://help.github.com/git-ignore/)
* [Learn Git](http://learn.github.com/)


### Setup Heroku

1. Create an account at http://api.heroku.com/signup
2. sudo gem install heroku

Inside your project folder:

1. heroku create => This will create a new sub-domain like blah-232.heroku.com and setup everything
2. git push heroku master => This will push the code to heroku


### Clone Pastie Tutorial

I sent you this [link](http://blog.zerosum.org/2008/7/2/clone-pastie-with-sinatra-datamapper-redux) already, but I would highly recommend going through it and get that working. You will need to install datamapper and sqlite3. I ran into one library issue with these, and I found an easy fix... but I can't find the link. So if you do get an error let me know and we'll find that fix (it was instally another library I think). You could even start with something a lot [easier](http://blog.heroku.com/archives/2009/3/5/32_deploy_merb_sinatra_or_any_rack_app_to_heroku/) too.

With the Pastie clone, you will have to make one change:

	DataMapper.setup(:default, ENV['DATABASE_URL'] || 'sqlite3://database_name.db')

Why? Because [Heroku doesn't allow and writable files](http://docs.heroku.com/database) except log files, so you will have to use their database which is found via that DATABASE_URL environment variable path. The '||' allows you to use your local db when on your box.

Besides that, I think everything else should work. Let me know if not though!!

### Various Tools

* [RadRails IDE](http://www.radrails.org/)
* [Ruby RegEx Tool](http://rubular.com/)
* [Ruby Metrics (Advanced, don't look at this now!)](http://getcaliper.com/caliper)
* [Ruby Library Comparision](http://www.ruby-toolbox.com/)
* [Ruby IRB Tricks & Tools](http://utilitybelt.rubyforge.org/)
* [More IRB Links](http://www.rubyinside.com/irb-lets-bone-up-on-the-interactive-ruby-shell-1771.html)
