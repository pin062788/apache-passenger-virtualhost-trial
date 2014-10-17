* Config Locale

    sudo locale-gen en_US
    sudo apt-get update
    sudo locale-gen en_US en_US.UTF-8 en_CA.UTF-8
    sudo dpkg-reconfigure locales

* Prepare environment

    sudo apt-get install apache2 curl git build-essential zlibc zlib1g-dev zlib1g libcurl4-openssl-dev libssl-dev libopenssl-ruby apache2-prefork-dev libapr1-dev libaprutil1-dev libreadline6 libreadline6-dev

    sudo apt-get install build-essential libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison

   	sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties

* Install Ruby 2.0

    ruby -v
    wget ftp://ftp.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p0.tar.gz
    tar xzvf ruby-2.0.0-p0.tar.gz
    cd ruby-2.0.0-p0
    ./configure
    make
    sudo make install
    ruby -v
    which ruby
    ls -al /usr/bin/ruby
    which ruby
    ls -al /usr/local/bin/ruby
    ls /usr/local/bin/ruby 
    ls /usr/local/bin/ruby -v
    /usr/local/bin/ruby -v
    ruby -v
    which ruby


* Create a new user
	adduser apache
	visudo //to set the user with root privileges
	apache ALL=(ALL:ALL) ALL // add the following line, granting all the permissions to your new user:

	Reference https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-12-04

* Setup Apache2 and Passenger
	sudo mkdir -p /var/www/example.com/public_html	

* Setup Passenger
	sudo gem install passenger	
	sudo passenger-install-apache2-module
	//created a file called /etc/apache2/mods-available/passenger.load
	`LoadModule passenger_module /usr/local/lib/ruby/gems/2.0.0/gems/passenger-4.0.0.rc4/libout/apache2/mod_passenger.so`

	//created a file called /etc/apache2/mods-available/passenger.conf


	sudo a2enmod passenger
	sudo service apache2 restart
	apache2ctl -t -D DUMP_MODULES //Check if passenger modules have been loaded

* Setup Virtual Host 
		Refer to this post https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts

	* moved the default apache page	
		sudo mkdir /var/www/default
		sudo mv /var/www/index.html /var/www/default/index.html
		//Create a new default directory
		//Create the configuatoin file
		/etc/apache2/sites-available/default.conf
		Check https://github.com/wldandan/apache-passenger-virtualhost-trial/blob/master/config/default


	* Create a new site by using virtual host
		sudo mkdir -p /var/www/example.com/public_html
		sudo chown -R $USER:$USER /var/www/example.com/public_html 
		sudo chmod -R 755 /var/www
		sudo vi /var/www/example.com/public_html/index.html
		sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/example.com
		sudo vi /etc/apache2/sites-available/example.com.conf
		sudo a2ensite example.com

	* Create a new site based on sinatra

	* Create a new site based on rails	