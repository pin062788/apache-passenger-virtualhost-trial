* 'apps' stores the different application. Usually, the application will be copyied to '/var/www'

* 'config' stores the relevant config file for the application respectively, which should be copied to '/etc/apache2/sites-available'

* execute 'sudo a2ensite <application>' to enable the application in apache

* edit /etc/hosts and add the mappings for the application

        <ip>  www.xxx.com   localhost

* execute 'curl www.xxx.com'
