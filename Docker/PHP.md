# PHP

### Dockerfile

```Dockerfile
FROM php:7.4-fpm-alpine

# RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
#     && apk add tzdata && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

RUN apk --no-cache add git freetype-dev libjpeg-turbo-dev libpng-dev libzip-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install mysqli gd pdo_mysql zip \
    && curl --silent --show-error https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

# RUN composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
```

### php-fpm.d/zz-docker.conf

```vim
[www]
listen = /var/run/php/php.sock
listen.mode = 0666
```
