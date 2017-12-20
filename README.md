# APACHE MYSQL PHP for development with Docker-compose

## Dependencies

* [Docker](https://www.docker.com/)
* [Docker Compose](https://docs.docker.com/compose/install/)

## How it works

### Download this repo

With git clone or download button

### Copy your source code into www folder

Create a 'www' folder and copy your source code into it or clone a repo into 'www' folder. Example with WordPress repository :

`git clone https://github.com/WordPress/WordPress www`

### Start the containers

For the first time, create the containers :

`docker-compose up -d`

If you have already created the containers you must to start the containers :

`docker-compose start`

After that you can visit http://localhost

### Access to PhpMyAdmin

Visit http://localhost:8080

### Change php.ini config (optional)

If you need to modify the php configuration you can modify the php-apache/php.ini. This file is mounted as php.ini file in the container.

### Change Apache document root (optional)

If you need to change the document root, you can modify the environment variable APACHE_DOCUMENT_ROOT in php-docker/Dockerfile. The value of APACHE_DOCUMENT_ROOT represent the path in the container. The path for www folder in the container is /var/www/html/. For example, if you need to change the document root for a folder named 'public' in the 'www' folder, the value for APACHE_DOCUMENT_ROOT must be /var/www/html/public/

After the modification, if you have already build the php-apache image with previous commands, you need to build again or up with docker-compose with the build option :

`docker-compose up --build`

### Database

#### Files backup

The files of the MySQL database in the container are mounted in the 'mysql/data' directory. This means that the database files are saved in the 'mysql/data' directory. If you remove the database container by accident, or do a `docker-compose rm`, you can do the `docker-compose up -d` command without affecting the information in the database.

#### Change the default database name (optional)

The default database name is 'project', you can modify the value of MYSQL_DATABASE in the docker-compose.yml file to change the default database name.

#### Change the database password for root (optional)

By default the root password of the MySQL database is 'root'. You can change the value of MYSQL_ROOT_PASSWORD and the value of PMA_PASSWORD (for automatic login in phpmyadmin) in the docker-compose.yml file.
