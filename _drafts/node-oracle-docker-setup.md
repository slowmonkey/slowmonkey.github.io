
```
FROM debian:10-slim as buildstage

RUN apt update \
    && apt -y install unzip wget libaio1 \
    && mkdir -p downloads \
    && wget -P /downloads https://download.oracle.com/otn_software/linux/instantclient/216000/instantclient-basiclite-linux.x64-21.6.0.0.0dbru.zip \
    && cd /downloads \
    && unzip instantclient-basiclite-linux.x64-21.6.0.0.0dbru.zip \
    && rm instantclient-basiclite-linux.x64-21.6.0.0.0dbru.zip



FROM node:18-slim

WORKDIR /app

ENV PATH /app/node_modules/.bin:$PATH
ENV LD_LIBRARY_PATH=/lib/instantclient_21_6

COPY --from=buildstage /downloads /lib
COPY --from=buildstage /usr/lib/x86_64-linux-gnu/libaio* /lib/instantclient_21_6

COPY /src/package*.json .

RUN npm install
```