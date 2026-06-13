# Lab13

##CZĘŚĆ OBOWIĄZKOWA
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker compose pull
[+] pull 60/60
 ✔ Image mysql:8.4         Pulled                                                                                  18.8s
 ✔ Image php:8.3-fpm       Pulled                                                                                  15.7s
 ✔ Image nginx:1.27-alpine Pulled                                                                                  5.0ss
 ✔ Image phpmyadmin:5.2    Pulled                                                                                  18.4s
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker images
                                                                                                    i Info →   U  In Use
IMAGE                              ID             DISK USAGE   CONTENT SIZE   EXTRA
alpine:latest                      25109184c71b       13.1MB         3.95MB    U
fallfinch/lab5-stage1:v1           aa7bfff3c5a2       13.3MB         3.94MB
fallfinch/lab5-stage2:v1           791fef35aba3       92.9MB         26.1MB
fallfinch/lab5/stage1:v1           5c707716507a       13.3MB         3.94MB
fallfinch/lab5:v1                  f92236273316        269MB         64.9MB    U
fallfinch/lab:genius.v1.0.0        bc45d248c4e1        240MB         65.8MB    U
fallfinch/stage1:v1                167e3e33de26       13.3MB         3.94MB
fallfinch/web100:latest            8a924fc64d51        269MB         64.9MB    U
fallfinch/web:v4                   6660c9dec2f5        256MB         62.5MB
fallfinch/web:v5                   a15f6fa0fddf        256MB         62.5MB
fallfinch/web:v6                   c1e1ba18041d        264MB           65MB    U
gcr.io/cadvisor/cadvisor:v0.47.1   daee1ca59659        122MB           34MB    U
grafana/grafana:latest             5dad0df181cb       1.47GB          352MB    U
hello-world:latest                 85404b3c5395       25.9kB         9.52kB    U
local/first:v1.0.0                 941b8d2e2710       6.77MB         2.21MB
local/mynginx:latest               175274af2b52       16.1MB         4.74MB
local/test:v1.0.0                  e7785f54cef9       11.1MB         3.38MB    U
local/test:v1.0.1                  18200fb24d87       11.1MB         3.38MB
local/test:v1.0.2                  55939591c227       11.4MB         3.41MB
moby/buildkit:buildx-stable-1      0039c1d47e87        354MB          111MB    U
mysql:8.4                          c36050afdca8       1.12GB          254MB
nginx:1.27-alpine                  65645c7bb6a0       74.5MB         21.9MB
nginx:latest                       bc45d248c4e1        240MB         65.8MB    U
php:8.3-fpm                        61cabe26e713        703MB          179MB
phpmyadmin:5.2                     c9f2c3790e7b        821MB          197MB
prom/prometheus:latest             69f524141883        593MB          156MB    U
redis:latest                       315270d16608        204MB         55.3MB    U
ubuntu:latest                      d1e2e92c075e        119MB         31.7MB    U
weatherapp:latest                  d16332d0fa69        205MB         62.4MB    U
web100:latest                      8a924fc64d51        269MB         64.9MB    U
web:stage1                         f5d2372a30fb       13.3MB         3.94MB
web:v5                             871d3a9d76fa       92.8MB         26.1MB    U
web:v6                             0dc31d6ac2d3       92.9MB         26.1MB    U
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker compose up -d
[+] up 7/7
 ✔ Network lab13_backend   Created                                                                                  0.0s
 ✔ Network lab13_frontend  Created                                                                                  0.0s
 ✔ Volume lab13_mysql_data Created                                                                                  0.0s
 ✔ Container php           Started                                                                                  0.4s
 ✔ Container mysql         Started                                                                                  0.4s
 ✔ Container phpmyadmin    Started                                                                                  0.6s
 ✔ Container nginx         Started                                                                                  0.7s
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker ps
CONTAINER ID   IMAGE                              COMMAND                  CREATED          STATUS                   PORTS                                         NAMES
c05db43ba1a1   phpmyadmin:5.2                     "/docker-entrypoint.…"   10 seconds ago   Up 9 seconds             0.0.0.0:6001->80/tcp, [::]:6001->80/tcp       phpmyadmin
450ec6d7f42d   nginx:1.27-alpine                  "/docker-entrypoint.…"   10 seconds ago   Up 9 seconds             0.0.0.0:4001->80/tcp, [::]:4001->80/tcp       nginx
5c958af16663   php:8.3-fpm                        "docker-php-entrypoi…"   10 seconds ago   Up 9 seconds             9000/tcp                                      php
3eb728c92fdd   mysql:8.4                          "docker-entrypoint.s…"   10 seconds ago   Up 9 seconds             3306/tcp, 33060/tcp                           mysql
03f58ec5b18e   grafana/grafana                    "/run.sh"                2 days ago       Up 6 minutes             0.0.0.0:3000->3000/tcp, [::]:3000->3000/tcp   grafana
ab5edefa719a   prom/prometheus                    "/bin/prometheus --c…"   2 days ago       Up 6 minutes             9090/tcp                                      prometheus
c84a1b48e2da   gcr.io/cadvisor/cadvisor:v0.47.1   "/usr/bin/cadvisor -…"   2 days ago       Up 6 minutes (healthy)   8080/tcp                                      cadvisor
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker network ls
NETWORK ID     NAME             DRIVER    SCOPE
7307f2071398   bridge           bridge    local
d5128923d5ca   compose_back     bridge    local
d529c9ac02db   compose_front    bridge    local
a867d02e98ac   host             host      local
b804871b9c74   lab12net         bridge    local
2ad0aef8ff47   lab12net_2       bridge    local
3b045ea5e2bc   lab13_backend    bridge    local
843e0e348c03   lab13_frontend   bridge    local
3948a8584d86   none             null      local
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker network inspect lab13-lemp_backend
[]
Error response from daemon: network lab13-lemp_backend not found
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker network inspect lab13_backend
[
    {
        "Name": "lab13_backend",
        "Id": "3b045ea5e2bcd156f57a3c4519faecfcd553cad6f76820ec03f148a015e1e0c3",
        "Created": "2026-06-13T11:44:02.320718727+02:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv4": true,
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.22.0.0/16",
                    "Gateway": "172.22.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Options": {},
        "Labels": {
            "com.docker.compose.config-hash": "303a5c6a665d112f4cfee901befcc7bb1f43b97b72bbbccd3bbe862f5d0e35b7",
            "com.docker.compose.network": "backend",
            "com.docker.compose.project": "lab13",
            "com.docker.compose.version": "5.1.0"
        },
        "Containers": {
            "3eb728c92fdd759e94e52aa38a2d2f949f071fbe4fa6235c2d17a8bd1bd9aa48": {
                "Name": "mysql",
                "EndpointID": "21517562cf19f36594125e235956748721722666e095cbb26b94eea14c9e8741",
                "MacAddress": "ea:b5:08:e9:dc:1c",
                "IPv4Address": "172.22.0.2/16",
                "IPv6Address": ""
            },
            "450ec6d7f42dbe03d0d655a9e0fbd5a912a9d29cf236d5cbe79cf2f33e4739f1": {
                "Name": "nginx",
                "EndpointID": "0eefe94f3a74c1666b0271488e6138e2bd74f7ea6c9ff78256629d354477ab1e",
                "MacAddress": "46:33:6d:41:c0:5d",
                "IPv4Address": "172.22.0.5/16",
                "IPv6Address": ""
            },
            "5c958af166633e0e38306b5f1fb2a470922cb3d8b88490fea5ad73238fdde74a": {
                "Name": "php",
                "EndpointID": "81bfdb77deaa938921bd0a8d9fa37c9b647f861adbb36056447df9359daa4ed9",
                "MacAddress": "1a:f5:ee:40:7e:a7",
                "IPv4Address": "172.22.0.3/16",
                "IPv6Address": ""
            },
            "c05db43ba1a1a55200cfeea539a47517c0163ce94ff7d8c9df5ad4030bf7709d": {
                "Name": "phpmyadmin",
                "EndpointID": "a4f8367003f6abbb330babbe291b8c41c4c62178836a499438401c1f189dc0cf",
                "MacAddress": "ae:a8:67:c1:16:2c",
                "IPv4Address": "172.22.0.4/16",
                "IPv6Address": ""
            }
        },
        "Status": {
            "IPAM": {
                "Subnets": {
                    "172.22.0.0/16": {
                        "IPsInUse": 7,
                        "DynamicIPsAvailable": 65529
                    }
                }
            }
        }
    }
]
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker network inspect lab13_frontend
[
    {
        "Name": "lab13_frontend",
        "Id": "843e0e348c03966288a3dfb5e1bc77b0048ba5e8f75106f0ef1dcaa484bc7010",
        "Created": "2026-06-13T11:44:02.352430514+02:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv4": true,
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.24.0.0/16",
                    "Gateway": "172.24.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Options": {},
        "Labels": {
            "com.docker.compose.config-hash": "c99dfed360a6944db43f183a5bd3f4016b0c10584adeeaa2e535a0bc34386287",
            "com.docker.compose.network": "frontend",
            "com.docker.compose.project": "lab13",
            "com.docker.compose.version": "5.1.0"
        },
        "Containers": {
            "450ec6d7f42dbe03d0d655a9e0fbd5a912a9d29cf236d5cbe79cf2f33e4739f1": {
                "Name": "nginx",
                "EndpointID": "ca416ff47a73954f7eee82656c2ac5e1e7b5dd90f1b8055f6d4956d14981866e",
                "MacAddress": "1a:b9:d5:32:50:ca",
                "IPv4Address": "172.24.0.3/16",
                "IPv6Address": ""
            },
            "c05db43ba1a1a55200cfeea539a47517c0163ce94ff7d8c9df5ad4030bf7709d": {
                "Name": "phpmyadmin",
                "EndpointID": "65014def77be2ec40c35fa2e715fc51639020063c122925cdc3df6a6b9fd803c",
                "MacAddress": "d6:4c:49:92:f9:88",
                "IPv4Address": "172.24.0.2/16",
                "IPv6Address": ""
            }
        },
        "Status": {
            "IPAM": {
                "Subnets": {
                    "172.24.0.0/16": {
                        "IPsInUse": 5,
                        "DynamicIPsAvailable": 65531
                    }
                }
            }
        }
    }
]
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker exec -it mysql mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 32
Server version: 8.4.9 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```
```
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| laboratorium13     |
| mysql              |
| performance_schema |
| sys                |
| testdb             |
+--------------------+
6 rows in set (0.00 sec)
```
```
mysql> docker compose down
    -> ^C
mysql> ^C
mysql> exit
Bye
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker compose down
[+] down 6/6
 ✔ Container phpmyadmin   Removed                                                                                   1.6s
 ✔ Container nginx        Removed                                                                                   0.7s
 ✔ Container php          Removed                                                                                   0.2s
 ✔ Container mysql        Removed                                                                                   1.6s
 ✔ Network lab13_frontend Removed                                                                                   0.3s
 ✔ Network lab13_backend  Removed                                                                                   0.5s
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$
```
##CZĘŚĆ NIEOBOWIĄZKOWA
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker compose config
name: lab13
services:
  mysql:
    container_name: mysql
    environment:
      MYSQL_DATABASE: testdb
      MYSQL_PASSWORD_FILE: /run/secrets/mysql_password
      MYSQL_ROOT_PASSWORD_FILE: /run/secrets/mysql_root_password
      MYSQL_USER_FILE: /run/secrets/mysql_user
    image: mysql:8.4
    networks:
      backend: null
    restart: always
    secrets:
      - source: mysql_root_password
        target: /run/secrets/mysql_root_password
      - source: mysql_user
        target: /run/secrets/mysql_user
      - source: mysql_password
        target: /run/secrets/mysql_password
    volumes:
      - type: volume
        source: mysql_data
        target: /var/lib/mysql
        volume: {}
  nginx:
    container_name: nginx
    depends_on:
      php:
        condition: service_started
        required: true
    image: nginx:1.27-alpine
    networks:
      backend: null
      frontend: null
    ports:
      - mode: ingress
        target: 80
        published: "4001"
        protocol: tcp
    volumes:
      - type: bind
        source: /mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13/php
        target: /var/www/html
        bind: {}
      - type: bind
        source: /mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13/nginx/default.conf
        target: /etc/nginx/conf.d/default.conf
        bind: {}
  php:
    container_name: php
    image: php:8.3-fpm
    networks:
      backend: null
    volumes:
      - type: bind
        source: /mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13/php
        target: /var/www/html
        bind: {}
  phpmyadmin:
    container_name: phpmyadmin
    depends_on:
      mysql:
        condition: service_started
        required: true
    environment:
      PMA_HOST: mysql
    image: phpmyadmin:5.2
    networks:
      backend: null
      frontend: null
    ports:
      - mode: ingress
        target: 80
        published: "6001"
        protocol: tcp
networks:
  backend:
    name: lab13_backend
  frontend:
    name: lab13_frontend
volumes:
  mysql_data:
    name: lab13_mysql_data
secrets:
  mysql_password:
    name: lab13_mysql_password
    file: /mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13/secrets/mysql_password.txt
  mysql_root_password:
    name: lab13_mysql_root_password
    file: /mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13/secrets/mysql_root_password.txt
  mysql_user:
    name: lab13_mysql_user
    file: /mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13/secrets/mysql_user.txt
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker compose down -v
[+] down 1/1
 ✔ Volume lab13_mysql_data Removed                                                                                  0.0s
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker volume ls
DRIVER    VOLUME NAME
local     buildx_buildkit_weatherbuilder0_state
local     compose_grafana_data
local     compose_prometheus_data
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker compose up -d
[+] up 7/7
 ✔ Network lab13_backend   Created                                                                                  0.0s
 ✔ Network lab13_frontend  Created                                                                                  0.0s
 ✔ Volume lab13_mysql_data Created                                                                                  0.0s
 ✔ Container mysql         Started                                                                                  0.5s
 ✔ Container php           Started                                                                                  0.4s
 ✔ Container nginx         Started                                                                                  0.7s
 ✔ Container phpmyadmin    Started
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker exec -it mysql bash
bash-5.1# ls /run/secrets
mysql_password  mysql_root_password  mysql_user
bash-5.1# cat /run/secrets/mysql_root_password
root123bash-5.1# ^C
bash-5.1# ^C
bash-5.1# exit
exit
```
```
gil-a@LAPTOP-HU5MFDCI:/mnt/c/Users/gil-a/Desktop/Studia/Semestr 6/docker/lab13$ docker exec -it mysql mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.4.9 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```
```
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| testdb             |
+--------------------+
5 rows in set (0.02 sec)
```
```
mysql> SHOW DATABASES;
+-----------------------+
| Database              |
+-----------------------+
| information_schema    |
| laboratorium13_secret |
| mysql                 |
| performance_schema    |
| sys                   |
| testdb                |
+-----------------------+
6 rows in set (0.00 sec)

mysql>
```


