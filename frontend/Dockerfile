FROM node:18-alpine as builder

WORKDIR /app

COPY package*.json /app

RUN npm install

COPY . .

RUN npm run build

FROM nginx:alpine3.17

COPY --from=builder /app/build /usr/share/nginx/html

COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD [ "nginx","-g", "daemon off;" ]