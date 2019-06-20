FROM alpine:3.10

ENV NGINX_VERSION=1.16.0-r2

RUN apk --no-cache add \
  nginx=$NGINX_VERSION \
  && mkdir -p /run/nginx

EXPOSE 8787
CMD ["nginx", "-g", "daemon off;"]
