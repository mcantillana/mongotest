# Mongo DB

## Para levantar servicio
~~~
docker-compose up -d
~~~

## Para revisar logs
~~~
docker-compose logs -f
~~~

## Para revisar salud del contenedor
~~~
docker-compose ps 
~~~

## Para backups

### Con docker-compose
~~~
docker-compose exec mongo mongodump --host 127.0.0.1 --port 27017 --db demo  --authenticationDatabase admin --username root --password 1234 --archive > ./backups/demo.archive        
~~~

### Con docker
~~~
docker exec mongotest_mongo_1 sh -c 'mongodump --authenticationDatabase admin --username root --password 1234 --archive' > /tmp/db.dump
~~~

## Como restaurar un backup
~~~
docker exec -i mongotest_mongo_1 sh -c 'mongorestore --authenticationDatabase admin --username root --password 1234 --archive' < /tmp/db.dump
~~~

## referencias
* https://jeromejaglale.com/doc/programming/mongodb_docker_mongodump_mongorestore
* https://hub.docker.com/_/mongo