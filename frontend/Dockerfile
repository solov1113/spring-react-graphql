#!/bin/bash

FROM node:18.7.0-alpine as build
WORKDIR /app
COPY package.json ./
RUN yarn install --production
COPY . ./
RUN yarn build

FROM nginx:1.23.1-alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

