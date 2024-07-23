FROM node:20.15.1-alpine3.20@sha256:cf5e7b223dea2efc6a73c55c6655b740576fe9c2596927a53533feded0fb5f5f

RUN apk add --no-cache tini
USER node
WORKDIR /usr/src/app
COPY --chown=node:node package*.json ./
RUN npm ci
COPY --chown=node:node . .
ENV CHOKIDAR_USEPOLLING=true
EXPOSE 24678
EXPOSE 3000
ENTRYPOINT ["/sbin/tini", "--", "/bin/sh"]
