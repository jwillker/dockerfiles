FROM ubuntu
MAINTAINER John Willker <frazao.jhonn@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
#Update
RUN apt-get update
#Install NGINX
RUN apt-get -y install nginx

# Main package installation
RUN apt-get -y install php5-cgi mysql-server php5-mysql

# Extra package installation
RUN apt-get -y install php5-gd php-apc php5-mcrypt php5-fpm

# Nginx configuration
ADD default /etc/nginx/sites-available/

# PHP FastCGI script
#ADD php-fcgi /usr/local/sbin/
#RUN chmod o+x /usr/local/sbin/php-fcgi

# Basic PHP website
#ADD index.php /var/www/html/
#Restart nginx
RUN service nginx restart

# Create new MySQL admin user
RUN service mysql start; mysql -u root -e "CREATE USER 'admin'@'%' IDENTIFIED BY 'pass';";mysql -u root -e "GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' WITH GRANT OPTION;";

# MySQL configuration
RUN sed -i 's/bind-address/#bind-address/' /etc/mysql/my.cnf

EXPOSE 80 3306

#CMD [""]
