FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.config /etc/nginx/conf.d/default.config
COPY --from=builder /app/build /usr/share/nginx/html