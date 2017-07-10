# Kong Gateway Demo

## Setup

All the demo is based on the docker and docker network.

1. create sepcify netowkrs locally for different containers

```
docker network create micro-kong
```

2. start the Kong gate way.

```
docker-compose up --build
```

3. start the helloWorld service

```
cd services/helloServer

docker-compose up --build
```

4. registry the service in kong
```
docker exec -it helloserver_hello base

curl -i -X POST --url http://kong:8001/apis/ --data 'name=helloWorld' --data 'hosts=hello.com' --data 'upstream_url=http://hello:8080'
```

and then can test it out on the terminal 

```
http localhost:8000 host:hello.com
```