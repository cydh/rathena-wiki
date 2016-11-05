---
title: Setup LAMP on CentOS
permalink: /Setup_LAMP_on_CentOS/
---

Setup LAMP on CentOS
--------------------

LAMP is short for Linux, Apache, MySQL, PHP. This tutorial shows how you can install an Apache2 webserver on a CentOS server with PHP5 support (mod_php) and MySQL support.

##### 1. Installing MySQL 5

To install MySQL, we do this:

    yum install mysql mysql-server

Then we create the system startup links for MySQL (so that MySQL starts automatically whenever the system boots) and start the MySQL server:

    chkconfig --levels 235 mysqld on
    /etc/init.d/mysqld start

Set passwords for the MySQL root account:

    mysql_secure_installation

Then do it like this:

    [root@server1 ~]# mysql_secure_installation




    NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
          SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


    In order to log into MySQL to secure it, we'll need the current
    password for the root user.  If you've just installed MySQL, and
    you haven't set the root password yet, the password will be blank,
    so you should just press enter here.

    Enter current password for root (enter for none):
    OK, successfully used password, moving on...

    Setting the root password ensures that nobody can log into the MySQL
    root user without the proper authorisation.

    Set root password? [Y/n] <-- ENTER
    New password: <-- yourrootsqlpassword
    Re-enter new password: <-- yourrootsqlpassword
    Password updated successfully!
    Reloading privilege tables..
     ... Success!


    By default, a MySQL installation has an anonymous user, allowing anyone
    to log into MySQL without having to have a user account created for
    them.  This is intended only for testing, and to make the installation
    go a bit smoother.  You should remove them before moving into a
    production environment.

    Remove anonymous users? [Y/n] <-- ENTER
     ... Success!

    Normally, root should only be allowed to connect from 'localhost'.  This
    ensures that someone cannot guess at the root password from the network.

    Disallow root login remotely? [Y/n] <-- ENTER
     ... Success!

    By default, MySQL comes with a database named 'test' that anyone can
    access.  This is also intended only for testing, and should be removed
    before moving into a production environment.

    Remove test database and access to it? [Y/n] <-- ENTER
     - Dropping test database...
     ... Success!
     - Removing privileges on test database...
     ... Success!

    Reloading the privilege tables will ensure that all changes made so far
    will take effect immediately.

    Reload privilege tables now? [Y/n] <-- ENTER
     ... Success!

    Cleaning up...



    All done!  If you've completed all of the above steps, your MySQL
    installation should now be secure.

    Thanks for using MySQL!


    [root@server1 ~]#

#### 2. Installing Apache2

Apache2 is available as a CentOS package, therefore we can install it like this:

    yum install httpd

Now configure your system to start Apache at boot time...

    chkconfig --levels 235 httpd on

... and start Apache:

    /etc/init.d/httpd start

Now direct your browser to *<http://your-ip>* , and you should see the Apache2 placeholder page.

#### 3. Installing PHP5

We can install PHP5 and the Apache PHP5 module as follows:

    yum install php

We must restart Apache afterwards:

    /etc/init.d/httpd restart

#### 4. Getting MySQL Support In PHP5

To get MySQL support in PHP, we can install the php-mysql package. It's a good idea to install some other PHP5 modules as well as you might need them for your applications. You can search for available PHP5 modules like this:

    yum search php

Pick the ones you need and install them like this:

    yum install php-mysql php-gd php-imap php-ldap php-mbstring php-odbc php-pear php-xml php-xmlrpc

APC is a free and open PHP opcode cacher for caching and optimizing PHP intermediate code. It's similar to other PHP opcode cachers, such as eAccelerator and Xcache. It is strongly recommended to have one of these installed to speed up your PHP page.

APC can be installed as follows:

    yum install php-pecl-apc

Now restart Apache2:

    /etc/init.d/httpd restart

#### 5. phpMyAdmin

phpMyAdmin is a web interface through which you can manage your MySQL databases.

First we enable the RPMforge repository on our CentOS system as phpMyAdmin is not available in the official CentOS 6.3 repositories:

Import the RPMforge GPG key:

    rpm --import http://dag.wieers.com/rpm/packages/RPM-GPG-KEY.dag.txt

On x86_64 systems:

    yum install http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.2-2.el6.rf.x86_64.rpm

On i386 systems:

    yum install http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.2-2.el6.rf.i686.rpm

phpMyAdmin can now be installed as follows:

    yum install phpmyadmin

Now we configure phpMyAdmin. We change the Apache configuration so that phpMyAdmin allows connections not just from localhost (by commenting out the <Directory "/usr/share/phpmyadmin"> stanza):

    nano /etc/httpd/conf.d/phpmyadmin.conf

    #
    #  Web application to manage MySQL
    #

    #<Directory "/usr/share/phpmyadmin">
    #  Order Deny,Allow
    #  Deny from all
    #  Allow from 127.0.0.1
    #</Directory>

    Alias /phpmyadmin /usr/share/phpmyadmin
    Alias /phpMyAdmin /usr/share/phpmyadmin
    Alias /mysqladmin /usr/share/phpmyadmin

Next we change the authentication in phpMyAdmin from cookie to http:

    nano /usr/share/phpmyadmin/config.inc.php

    [...]
    /* Authentication type */
    $cfg['Servers'][$i]['auth_type'] = 'http';
    [...]

Restart Apache:

    /etc/init.d/httpd restart

Afterwards, you can access phpMyAdmin under *<http://your-ip/phpmyadmin/>*

That's all folks, I hope that this helps to make Web Server for RO up and running.