#Это так называемый мультистейдж docker-файл. Сначала делаем образ, который соберёт нам java-приложение,
#а затем из него берём собранный артефакт и кладём его в новый образ, чтобы оставить в нём меньше лишнего

# build
FROM node:8 as builder

COPY . /app
WORKDIR /app
RUN npm install && npm run build

FROM nginx:1.27
RUN rm -rf /usr/share/nginx/html && mkdir -p /usr/share/nginx/html
COPY --from=builder /app/dist/frontend/ /usr/share/nginx/html
