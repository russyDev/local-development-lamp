FROM ubuntu:22.04

ENV TZ=Europe/Kiev
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt update
RUN apt install -y --no-install-recommends php8.1
RUN apt update && apt install -y apache2 git zip unzip curl
RUN apt-get install -y php8.1-cli php8.1-common php8.1-mysql php8.1-zip libapache2-mod-php8.1  php8.1-gd php8.1-mbstring php8.1-curl php8.1-xml php8.1-bcmath

RUN curl -sS https://getcomposer.org/installer -o composer-setup.php && \
php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN a2enmod rewrite

WORKDIR /var/www/html

COPY ./apache2/000-default.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 80
ENTRYPOINT apachectl -D FOREGROUND
