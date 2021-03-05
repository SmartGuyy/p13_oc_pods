FROM alpine:3.13.2

RUN apk add --no-cache mysql-client

RUN apk add --no-cache  --repository http://dl-cdn.alpinelinux.org/alpine/edge/community php php-mysqli

RUN php -v

RUN mysql --version
