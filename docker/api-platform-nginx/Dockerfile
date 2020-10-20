FROM debian:jessie

ARG server_name

RUN apt-get update && apt-get install -y \
    nginx

ADD nginx.conf /etc/nginx/
ADD symfony.conf /etc/nginx/sites-available/

RUN sed -i -e"s/SERVER_NAME/${server_name}/" /etc/nginx/sites-available/symfony.conf && \
    ln -s /etc/nginx/sites-available/symfony.conf /etc/nginx/sites-enabled/symfony && \
    rm /etc/nginx/sites-enabled/default && \
    echo "upstream php-upstream { server api-platform-php:9000; }" > /etc/nginx/conf.d/upstream.conf && \
    usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443