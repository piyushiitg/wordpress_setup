
--------- Wordpress blog setup for any site with mysql and postgresql ----------------------

1. sudo apt-get install php5, apache2

2. Database setup
=============== Setup for Mysql 5 ======================
1. sudo apt-get install mysql-server mysql-common mysql-client php5-mysql

2. Mysql database and user creation

   CREATE DATABASE tutrrblog;

   GRANT ALL ON tutrrblog.* TO wordpressuser@localhost IDENTIFIED BY 'root123';
3. Login to the db

    mysql -u wordpressuser -p
========================================================

=============== Setup for postgresql 9.1 ===============

1. sudo apt-get install postgresql-9.1, phppgadmin, postgresql-client-common, 

2. Download postgresql plugin for wordpress
wget "http://downloads.wordpress.org/plugin/postgresql-for-wordpress.1.3.0.zip"

3. sudo unzip postgresql-for-wordpress.1.3.0.zip 

4. sudo mv postgresql-for-wordpress/pg4wp/ blog/wp-content/

5. sudo cp blog/wp-content/pg4wp/db.php blog/wp-content/

6. vim db.php

define('DB_DRIVER', 'pgsql'); #mysql is other driver

7. create user and database in postgresql

CREATE DATABASE tutrrblog;
CREATE USER wordpressuser WITH PASSWORD 'root123';
GRANT ALL PRIVILEGES ON DATABASE tutrrblog to wordpressuser;

8. login to the database

psql -d tutrrblog -U wordpressuser -h localhost -W

===========================================================


3. wget "http://wordpress.org/latest.zip"

4. sudo unzip latest.zip

5. cd wordpress/

6. sudo mv wp-config-sample.php wp-config.php

7. vim wp-config.php

  Do these changes
  define('DB_NAME', 'tutrrblog');
  
  /** MySQL database username */
  define('DB_USER', 'wordpressuser');
  
  /** MySQL database password */
  define('DB_PASSWORD', 'root123');
  
  /** MySQL hostname */
  define('DB_HOST', 'localhost');


8. sudo mv wordpress/ blog/

9. sudo cp -r blog/ /var/www/blog/

10. Run install.php file for final setup of wordpress

http://localhost/blog/wp-admin/install.php

10. Configure the apache vhost entry for blog

Yipeeeeeeee Your blog is ready ...........................
