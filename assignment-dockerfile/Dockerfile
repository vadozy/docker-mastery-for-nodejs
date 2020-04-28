# fill in the blanks to dockerize this node app
FROM node:10.15-alpine

RUN apk add --no-cache tini

EXPOSE 3000

WORKDIR /node

COPY package*.json ./

RUN mkdir app && chown -R node:node .
USER node

RUN npm install && npm cache clean --force

WORKDIR /node/app
COPY --chown=node:node app.js ./

ENTRYPOINT ["/sbin/tini", "--"]

CMD ["node", "app.js"]
