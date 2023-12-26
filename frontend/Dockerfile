#1st Stage
FROM node:14-alpine3.17 as build-stage
WORKDIR /app
COPY package.json /app/
RUN npm install
COPY . /app/
RUN npm run build

#2nd Stage
FROM nginx:alpine
COPY --from=build-stage /app/dist/angular-ecommerce /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
