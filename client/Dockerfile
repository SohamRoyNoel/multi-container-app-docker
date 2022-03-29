FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# COPY all build assets from builder phrase into nginx as it runs 
# automatically if the build item is there in '/usr/share/nginx/html'
COPY --from=builder /app/build /usr/share/nginx/html
