FROM node:alpine
WORKDIR /usr/src/app
COPY server.js package.json .
RUN npm install
CMD ["node","server.js"]
