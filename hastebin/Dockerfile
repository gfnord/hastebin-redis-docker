FROM node:alpine
MAINTAINER Gustavo Nobrega <gustavofn@gmail.com>

RUN apk --update add --no-cache git

# Add dockerize tool -------------------
RUN apk add --no-cache openssl
ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz

RUN git clone https://github.com/seejohnrun/haste-server.git /opt/haste
WORKDIR /opt/haste
RUN npm install
RUN rm -f /opt/haste/config.js
ADD conf/config.js /opt/haste/config.js

VOLUME ["/opt/haste"]

EXPOSE 80
CMD ["npm", "start"]
