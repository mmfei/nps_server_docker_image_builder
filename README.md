# This is a docker deployment for **npa server** [ehang-io/nps](https://github.com/ehang-io/nps) (NPS is a lightweight, high-performance, powerful intranet penetration proxy server, with a powerful web management terminal.)

![docker build](https://img.shields.io/docker/cloud/build/mmfei/nps_server.svg)
![docker automated](https://img.shields.io/docker/cloud/automated/mmfei/nps_server.svg)
![language](https://img.shields.io/badge/language-dockerfile-3572A5.svg)
![docker image size](https://img.shields.io/docker/v/mmfei/nps_server/latest)
![docker hub](https://img.shields.io/docker/pulls/mmfei/nps_server.svg)
![docker image size](https://img.shields.io/docker/image-size/mmfei/nps_server/latest.svg)
![github last commit](https://img.shields.io/github/last-commit/mmfei/nps_server_docker_image_builder.svg)

see in docker hub:  
[mmfei/nps_server](https://hub.docker.com/r/mmfei/nps_server)


## reconfigure
[document](https://ehang-io.github.io/nps/#/?id=nps)

# what is in container
```bash
## where is nps
/usr/bin/nps

## config path
/etc/nps/conf
```

## attention
```bash
# nps server is listening ports : 80 , 443 , 8024 , 8080
# please check firewall , allow ports[80,443,8024,8080] (Please don't disable firewall!!!):
firewall-cmd --list-ports

# allow ports
firewall-cmd --permanent --add-port=8080/tcp # allow 8080 port
firewall-cmd --permanent --add-port=8024/tcp # allow 8024 port
firewall-cmd --permanent --add-port=10150-10179/tcp # allow ports : 10150~10179
firewall-cmd --reload #
```

## admin dashboard (modify passwod , see build/conf/nps.conf)
```bash
# local test(or change your ip/domain):
http://localhost:8080
user: adminroot
password: 123QWEIOP
```


## docker run
```bash
# for linux (Using network = host)
docker run -d  -v $PWD/build/conf/:/etc/nps/conf/ --network host --name nps_server mmfei/nps_server

# for mac or windows (--network host : Linux Only)
docker run --rm  -v $PWD/build/conf/:/etc/nps/conf/ --name nps_server -p 8080:8080 -p 8024:8024 mmfei/nps_server /usr/bin/nps
```

## docker compose
```docker
version: "3"
services: 
  name: "nps_server"
  image: "mmfei/nps_server"
  networks: "host"
  ports:
    - "8080:8080"
  volumes:
    "./build/conf/:/etc/nps/conf/"
```
