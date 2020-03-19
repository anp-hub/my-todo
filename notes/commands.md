# Dokcer commands

```
docker run --name mywebapp -d 
    \ -p 8080:80 
    \ -v ~/Books/k8s_container/nginx/www:/usr/share/nginx/html 
    \ -e name1='val1' -e name2='val2' nginx

docker ps | grep mywebapp

docker exec -it mywebapp bash
docker exec mywebapp env
docker logs -f mywebapp

docker stop mywebapp
docker start mywebapp

docker rm mywebapp

docker rm $(docker ps -aq)

docker network ls
docker network create mynet
docker run -it --name busybox-a --net mynet busybox sh 
docker run -it --name busybox-b --net mynet busybox sh 

ping busybox-a # from busybox-b container

sudo screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty # to see docker0 inteface with ifconfig

docker images
docker rmi nginx
```
======================
# TODO Application

## Create a docker network
docker network create todo-net

## Start postgres 
docker run --network todo-net --name todo-postgres -p 5432:5432 -e POSTGRES_USER=todo -e POSTGRES_PASSWORD=todo1234 -e POSTGRES_DB=todo -d postgres:11.2

## Start redis cache
docker run --name todo-redis --network todo-net -d -p 6379:6379 redis:5.0.3

## Start elsticsearch
docker run --name todo-elsatic --network todo-net -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:6.6.1

### Check the containers in the todo-net
docker network inspect todo-net



