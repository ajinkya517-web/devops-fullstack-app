# syntax=docker/dockerfile:1
FROM node:14.17.0 as build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Serve build with nginx
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 3000
CMD ["nginx", "-g", "daemon off;"]