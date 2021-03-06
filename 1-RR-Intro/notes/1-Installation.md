# Ruby on Rails Installation Process

We are using a Ubuntu machine for this installation and practice.

Install Ruby on Rails using "rbenv" on Ubtuntu:
-----------------------------------------------

- Install the required packages and pre-requisites:
```  
	sudo apt-get update -y
	sudo apt-get install -y git gitk
	sudo apt-get install -y gcc build-essential libpq-dev libssl-dev libreadline-dev libsqlite3-dev zliblg-dev
```
- Clone the rbenv repository:
```
	git clone git://github.com/sstephenson/rbenv.git /GitHub/ruby/.rbenv
```
- Export the RECIPE PUPPY site with port to bashrc:	
```
	echo 'export RECIPEPUPPY_HOSTPORT=www.recipepuppy.com:80' >> ~/.bashrc
```
- Export rbenv/bin:
```
	echo 'export PATH="$PATH:/GitHub/ruby/.rbenv/bin"' >> ~/.bashrc
	echo 'eval "$(rbenv init .)"' >> ~/.bashrc
```
- Now clone the ruby-build repository:
```
	git clone git://github.com/sstephenson/ruby-build.git /GitHub/ruby/.rbenv/plugins/ruby-build
```
- Set path for this plugins directory:
```
	echo 'export PATH="$PATH:/GitHub/ruby/.rbenv/plugins/ruby-build/bin"' >> ~/.bashrc
```
- Now we need to source the bashrc as we have some entries into it.:
```
	source ~/.bashrc
```
- Lets begin the installation now:
```
	rbenv install -v 2.2.2
```
- Lets set the default version of Ruby:
```
	rbenv global 2.2.2
	ruby -v
```
- We need to stop the gems to generate local documentation:
```
	echo "gem: --no-document" > ~/.gemrc
```
- Install the Ruby gem manager:
```
	gem install bundler
```
- Install Rails:
```
	gem install rails -v 4.2.3
```
- Now we need to rehash as it will let us to get command completion which relates to rails.
```
	rbenv rehash
```
- Let us install some other packages which are needed in our practice
```
	sudo apt-get install -y software-properties-common python-software-properties
```
- Now let us install some javascripts through a custom location
```
	sudo add-apt-repository ppa:chris-lea/node.js
	sudo apt-get install -y node.js
	sudo apt-get install -y bzip2
```
- Let us setup path for some ENV
```
	echo 'export PHANTOM_JS="phantomjs-1.9.8-linux-x86-64"' >> ~/.bashrc
```
- Let us download and install the PhantomJS package:
```
	cd /tmp
	curl -L https://bitbucket.org/ariya/phantomjs/downloads/$PHANTOM_JS.tar.bz2 | tar -xjvf
	sudo mv $PHANTOM_JS /usr/local/share
	sudo ln -s /usr/local/share/$PHANTOM_JS/bin/phantomjs /usr/local/bin
	phantomjs -v
```
- Install text editor:
```
	curl http://c758482.r82.cf2.rackcdn.com/Sublime%20Text%202.0.2%20x64.tar.bz2 | tar -xjf
	sudo mv 'Sublime Text 2' /opt/SublimeText2
	echo 'export PATH=$PATH:/opt/SublimeText2' >> ~/.bashrc
	source ~/.bashrc
```	
- Let us check all the versions now
```
	git --version
	phantomjs -v
	ruby -v
	rails -v
```
- Now let us create a rails application

	Create a project directory and then create a application
```
	mkdir /u01/ruby/projects &&cd /u01/ruby/projects

	rails new test-install -q
```
>	NOTE: Here we are using -r to run this command in quite mode as it will produce lot of output.
	
-	Now cd into the new rails application we have created and run the server
```
	cd test-install ; rails server
```
-	Let us check the application in the browser
```	
	http://localhost:3000
```
- Now we have completed configuring ruby on rails.