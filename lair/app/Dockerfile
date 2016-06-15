FROM node:0.10.41

WORKDIR /root/app

RUN curl -SLO "https://github.com/lair-framework/lair/releases/download/v2.4.1/lair-v2.4.1-linux-amd64.tar.gz" \
    && tar -zxf lair-v2.4.1-linux-amd64.tar.gz \
    && cd bundle/programs/server \
    && npm i

ENV ROOT_URL=http://0.0.0.0
ENV PORT 11014
EXPOSE 11014
CMD MONGO_URL=mongodb://$MONGO_PORT_27017_TCP_ADDR:$MONGO_PORT_27017_TCP_PORT/lair MONGO_OPLOG_URL=mongodb://$MONGO_PORT_27017_TCP_ADDR:$MONGO_PORT_27017_TCP_PORT/local node /root/app/bundle/main.js
