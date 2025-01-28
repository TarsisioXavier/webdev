FROM nginx:stable-alpine

RUN apk update \
    && apk upgrade \
    && apk add --no-cache \
    openssl \
    curl \
    bash \
    bash-completion

RUN set -x ; \
    addgroup -g 1000 -S www-data ; \
    adduser -u 1000 -D -S -G www-data www-data && exit 0 ; exit 1

CMD ["nginx"]
