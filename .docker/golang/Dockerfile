FROM golang:1.17.2-alpine3.14

RUN apk update && apk upgrade && \
    apk add --no-cache bash git openssh

WORKDIR /var/www