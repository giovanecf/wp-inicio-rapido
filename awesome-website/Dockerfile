# syntax=docker/dockerfile:1

ARG AWESOME_WEBSITE_IMAGE_VERSION

FROM wordpress:$AWESOME_WEBSITE_IMAGE_VERSION AS base

RUN echo "BASE STAGE"

COPY ./local.ini /usr/local/etc/php/conf.d/local.ini


FROM base AS base_with_migration

RUN echo "BASE WITH MIGRATION STAGE"

COPY ./html/ /var/www/html/


FROM base AS dev

RUN echo "DEV STAGE"

# Install packages under Debian
RUN apt-get update && \
    apt-get -y install git

# Install XDebug from source as described here:
# https://xdebug.org/docs/install
# Available branches of XDebug could be seen here:
# https://github.com/xdebug/xdebug/branches
RUN cd /tmp && \
    git clone https://github.com/xdebug/xdebug.git && \
    cd xdebug && \
    git checkout xdebug_3_4 && \
    phpize && \
    ./configure --enable-xdebug && \
    make && \
    make install && \
    rm -rf /tmp/xdebug

COPY ./xdebug.ini /usr/local/etc/php/conf.d/

# Since this Dockerfile extends the official Docker image `wordpress`,
# and since `wordpress`, in turn, extends the official Docker image `php`,
# the helper script docker-php-ext-enable (defined for image `php`)
# works here, and we can use it to enable xdebug:
RUN docker-php-ext-enable xdebug