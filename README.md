# This is a nps server

![language](https://img.shields.io/docker/automated/mmfei/nps_server.svg)
![language](https://img.shields.io/badge/language-dockerfile-3572A5.svg)
![docker image size](https://img.shields.io/docker/v/mmfei/nps_server/latest)
![docker hub](https://img.shields.io/docker/pulls/mmfei/nps_server.svg)
![docker image size](https://img.shields.io/docker/image-size/mmfei/nps_server/latest.svg)
![github last commit](https://img.shields.io/github/last-commit/mmfei/nps_server_docker_image_builder.svg)

see in docker hub:  
[mmfei/nps_server](https://hub.docker.com/r/mmfei/nps_server)

# what is in container
```u
## where is nps
/usr/bin/nps
## config
/etc/nps/conf
## how to start?
nps start
```

## attention
```
# nps server is listening ports : 80 , 443 , 8024 , 8080
# please check firewall , allow ports[80,443,8024,8080] (Please don't disable firewall!!!):
firewall-cmd --list-ports

# allow ports
firewall-cmd --permanent --add-port=8080/tcp # allow 8080 port
firewall-cmd --reload #
```

## admin dashboard
```
http://<IP>:8080
```


## docker run
```
docker run -d -v "./build/conf/nps.conf:/etc/nps/nps.conf" --network host --name nps_server mmfei/nps_server
```

## docker compose
```
version: "3"
services: 
  name: "nps_server"
  image: "mmfei/nps_server"
  networks: "host"
  volumes:
    "./build/conf/nps.conf:/etc/nps/conf/nps.conf"
```
