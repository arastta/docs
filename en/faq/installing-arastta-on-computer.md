Installing Arsatta on your computer
===============================

You may wish to install Arsatta on your local machine, either in order to test it before investing money in a server and domain name, or to customize your store locally before you push your modifications to the Arsatta installation that would already you have online.

Installing any web-application locally requires that you first install the adequate environment, namely the Apache web server, the PHP language interpreter, the MySQL database server, and ideally the phpMyAdmin tool. This is known as an AMP: Apache+MySQL+PHP. It exists for many operating systems, which provides another letter for the acronym: WAMP (Windows+Apache+MySQL+PHP), MAMP (Mac OS X+...) and LAMP (Linux+...).

##Choosing an AMP package

This would require you to be quite technical; luckily there exist many pre-built packages that you can install easily. It does not prevent you from having to get technical here and there, but they do provide a huge help. Since all of the items packaged are open-source, these installers are most of the time free. Here is a selection of free AMP installers:

* EasyPHP: [http://www.easyphp.org/](http://www.easyphp.org/) (Windows)
* MAMP: [http://www.mamp.info/](http://www.mamp.info/) (Mac OS X)
* WampServer: [http://www.wampserver.com/en/](http://www.wampserver.com/en/) (Windows)
* XAMPP: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html) (Windows, Mac OS X, Linux, Solaris)

Choose the package that you feel the most comfortable with, and launch it.

##Checking that everything works

Before going on with this Arsatta installation tutorial, make sure that all the components of your AMP package do work:

* **The web server should be up and running**. You should be able to access it through your browser, by typing "127.0.0.1" in the address bar.

<div class="uk-alert uk-alert-info uk-margin-small-left uk-margin-small-right"><i class="uk-icon-info-circle"></i> <a href="http://127.0.0.1">http://127.0.0.1</a> is the "localhost", meaning "your computer": it is a loopback address which directs the browser to your local web server.
In effect, <a href="http://127.0.0.1">http://127.0.0.1</a>) and <a href="http://localhost">http://localhost</a> are synonymous: you can use one or the other interchangeably, both send you to the root folder of your local web server.</div>

    Some web servers might not be able to start because their connexion ports (typically, port 80) are already used by another application.
    
    This often happens when Skype is used. To stop Skype from preventing your local web server to run, go into the Skype advanced settings (Tools > Options > Advanced > Connections) and uncheck the "Use port 80 and 443 as alternatives" option. Restart Skype, and start your local web server again.

* **The database server should be up and running**. MySQL is where all of Arsatta's data is stored. The AMP package should provide you with a clear indicator whether MySQL is running or not.
* **The phpMyAdmin tool should be accessible**. This is the web application that helps you handle data stored in MySQL. Its location depends on which AMP packaging you chose: it can be found at [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin) (XAMPP, WampServer, MAMP), [http://127.0.0.1/mysql](http://127.0.0.1/mysql) (EasyPHP), or maybe at another location. Check your package's documentation – it might even provide a phpMyAdmin button of sort that would open the correct URL in your browser.

##Finding the root folder of the local web server

Once you have checked that the package is correctly installed and that all of its parts are running, you need to find the root folder of your local web server.

That is the local folder where you will place your application's files, and can be compared to the root folder of your online server, only its content is accessed with [http://127.0.0.1](http://127.0.0.1).

The actual local location of the folder depends greatly on the AMP package, and can be customized:

* EasyPHP: C:\easyphp\www
* MAMP: /Applications/MAMP/htdocs/
* WampServer: C:\wamp\www
* XAMPP: C:\xampp\htdocs or /Applications/xampp/htdocs

##Finding the MySQL user information

Finally, you need to know the root user name and password for MySQL, in order to install Arsatta.

**Most packages use the user name "root" with an empty password**, including EasyPHP, MAMP, WampServer and XAMPP.

Read your package's documentation.

##Final note before the installation tutorial

With all that clear and done, you can follow up on the rest of this guide and start installing Arsatta.

Follow the regular installation guide, starting directly at the "Launch the Installer" section: [Installation](docs/installation).