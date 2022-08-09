FROM ubuntu:18.04

EXPOSE 80
EXPOSE 443

RUN apt update -y

# Timezone
ENV TZ=Europe/Moscow
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# SSH
RUN apt install -y openssh-server
RUN passwd & echo 12345678 & echo 12345678

# Nano
RUN apt install -y nano

# Git
RUN apt install -y git

# nginx
RUN apt install -y nginx

# Stop nginx
RUN service nginx stop

# Copy nginx completed configs
COPY etc/nginx/nginx.conf /etc/nginx/nginx.conf
COPY etc/nginx/sites-available/default /etc/nginx/sites-available/default

# Add repositories for PHP 8.1
RUN apt install lsb-release ca-certificates apt-transport-https software-properties-common -y
RUN add-apt-repository ppa:ondrej/php
RUN apt install -y -q unzip

# PHP 8.1
RUN apt install -y php8.1 php8.1-cli php8.1-mbstring php8.1-common php8.1-gd php8.1-fpm php8.1-curl php8.1-mysql

# php8.1-fpm
COPY etc/php/8.1/fpm/pool.d/www.conf /etc/php/8.1/fpm/pool.d/www.conf

# Start
CMD service nginx start && service php8.1-fpm start && service ssh start && /bin/bash