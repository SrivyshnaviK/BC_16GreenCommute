FROM node:10-alpine as builder
RUN mkdir /greencommute_fe/app 
RUN mv ./greencommute_fe/node_modules ./greencommute_fe/app
WORKDIR /app
COPY ./greencommute_fe/package.json  ./
RUN npm install --silent 
RUN npm install react-scripts@3.0.1 -g

COPY . .
RUN npm run build-dev --silent




FROM nginx
RUN rm -rf /usr/share/nginx/html/*
COPY --from=builder /app/dist /usr/share/nginx/html
RUN rm /etc/nginx/conf.d/default.conf
COPY ./greencommute_fe/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
