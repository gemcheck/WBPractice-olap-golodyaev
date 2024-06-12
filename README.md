## 2 Задание

### Поднятие контейнеров

docker run -d   --name nginx   --restart unless-stopped   -p 8080:80   -v /host/path1:/container/path1   --memory="512m" --cpus="1.0"   nginx

docker run -d   --name clickhouse   --restart unless-stopped   -p 8123:8123 -p 9000:9000   -v /host/clickhouse:/var/lib/clickhouse   --memory="1g" --cpus="2.0"   yandex/clickhouse-server

### Перезапуск 

docker restart nginx
docker restart clickhouse

### Удаление

docker stop nginx clickhouse
docker rm nginx clickhouse

## 3 Задание

### Создание docker-compose.yml

mkdir docker-compose-study
cd docker-compose-study
nano docker-compose.yml

### Сожержание файла docker-compose.yml

[Ссылка yml файл](https://github.com/gemcheck/WBPractice-olap-golodyaev/blob/main/docker-compose-study/docker-compose.yml)
---------------------------------------------------------------------------------
version: '3.8'

services:
  nginx:
    image: nginx
    container_name: nginx_container
    restart: unless-stopped
    ports:
      - "8080:80"
    volumes:
      - /host/nginx:/usr/share/nginx/html
    deploy:
      resources:
        limits:
          cpus: '1.0'
          memory: 512M

  clickhouse:
    image: yandex/clickhouse-server
    container_name: clickhouse_container
    restart: unless-stopped
    ports:
      - "8123:8123"
      - "9000:9000"
    volumes:
      - /host/clickhouse:/var/lib/clickhouse
    deploy:
      resources:
        limits:
          cpus: '2.0'
          memory: 1G
---------------------------------------------------------------------------------
### Запуск контейнеров

docker-compose up -d

### Остановка
docker-compose down
