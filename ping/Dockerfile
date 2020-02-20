FROM alpine:latest
LABEL maintainer marko

ENV HOST=""

RUN apk update \
&& apk add iputils bind-tools

CMD /bin/sh -c "echo HOST: && echo ${HOST} && echo IP address: && dig +short ${HOST} && ping ${HOST}"