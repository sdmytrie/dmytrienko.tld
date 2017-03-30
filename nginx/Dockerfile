# nginx/Dockerfile
FROM debian:jessie

MAINTAINER Serge D. <serge@dmytrienko.fr>

RUN apt-get update && apt-get install -y \
    nginx

    ADD nginx.conf /etc/nginx/
    ADD money-pp.dmytrienko.tld.conf /etc/nginx/sites-available/

    RUN ln -s /etc/nginx/sites-available/money-pp.dmytrienko.tld.conf /etc/nginx/sites-enabled/money-pp.dmytrienko.tld
    RUN rm /etc/nginx/sites-enabled/default

    RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

    RUN usermod -u 1000 www-data

    CMD ["nginx"]

    EXPOSE 80
    EXPOSE 443
