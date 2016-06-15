FROM alpine:latest

EXPOSE 11015

 RUN apk --update add curl && rm -fr /var/cache/apk/*
 RUN curl -Lo /usr/bin/api-server https://github.com/lair-framework/api-server/releases/download/v1.1.0/api-server_linux_amd64 \
     && chmod +x /usr/bin/api-server
CMD MONGO_URL=mongodb://$MONGO_PORT_27017_TCP_ADDR:27017/lair API_LISTENER=0.0.0.0:11015 /usr/bin/api-server
