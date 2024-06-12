## 2 Задание

### Поднятие контейренов

docker run -d   --name nginx   --restart unless-stopped   -p 8080:80   -v /host/path1:/container/path1   --memory="512m" --cpus="1.0"   nginx

docker run -d   --name clickhouse   --restart unless-stopped   -p 8123:8123 -p 9000:9000   -v /host/clickhouse:/var/lib/clickhouse   --memory="1g" --cpus="2.0"   yandex/clickhouse-server

### Перезапуск 

docker restart nginx
docker restart clickhouse

### Удаление

docker stop nginx clickhouse
docker rm nginx clickhouse