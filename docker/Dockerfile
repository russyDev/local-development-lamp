FROM ubuntu:20.04

ENV TZ=Europe/Kiev
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt update && apt install -y apache2 php libapache2-mod-php php-mysql php-cli curl php-curl php-xml php-mbstring git zip unzip php-zip
RUN curl -sS https://getcomposer.org/installer -o composer-setup.php && \
php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
a2enmod rewrite

WORKDIR /var/www/html

COPY ./apache2/000-default.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 80
ENTRYPOINT apachectl -D FOREGROUND
