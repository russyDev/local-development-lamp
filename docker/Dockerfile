FROM ubuntu:20.04
ENV TZ=Europe/Kiev
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt update && yes | apt install apache2
RUN apt update && yes | apt install php libapache2-mod-php php-mysql && apt install php-cli
RUN apt install curl && yes | apt-get install php-curl
RUN yes | apt install php-xml && yes | apt-get install php-mbstring
RUN yes | apt install git && yes | apt install zip unzip php-zip
RUN curl -sS https://getcomposer.org/installer -o composer-setup.php
RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN a2enmod rewrite
WORKDIR /var/www/html

COPY ./apache2/000-default.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 80
ENTRYPOINT apachectl -D FOREGROUND
