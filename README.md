# This is a nps server

see [mmfei/nps_server](https://hub.docker.com/r/mmfei/nps_server)

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
