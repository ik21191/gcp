FROM php:7.1.23-apache

EXPOSE 80
 
COPY ./my-static-site/ /var/www/html

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]