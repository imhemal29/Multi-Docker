FROM node:alpine as builder

WORKDIR '/app'

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx as run
EXPOSE 3000
COPY ./nginx/Default.conf   /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html