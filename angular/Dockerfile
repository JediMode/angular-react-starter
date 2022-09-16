# STAGE 1:BUILD
FROM node:16.17.0-alpine3.15 as node
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --prod

# STAGE 2:RUN
FROM nginx:alpine as ngi
VOLUME /var/cache/nginx
COPY --from=node /app/dist/angular-starter /usr/share/nginx/html
COPY ./nginx.conf  /etc/nginx/conf.d/default.conf
EXPOSE 80
