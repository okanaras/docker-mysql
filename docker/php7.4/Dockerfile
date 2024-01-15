FROM php:7.4-fpm 
# yaml da image vermemistik

# sunucudaki kutuphanelerin guncllenmesi gerek, soru sorarsa eger altina -y li de olusturduk
RUN apt-get update 
RUN apt-get upgrade -y

# laravel uyumlu calismasi icin
RUN apt-get install libzip-dev -y
RUN apt-get install zip unzip -y
RUN apt-get install -y git
RUN apt-get install -y curl

RUN docker-php-ext-install zip
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install bcmath
RUN docker-php-ext-install ctype
RUN docker-php-ext-install fileinfo
RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install tokenizer


RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN chown -R www-data:www-data /var/www/html
