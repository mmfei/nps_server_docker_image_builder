# nps client  | [nps server?](README.md)

## docker compose
### docker-compose.client.yml  (Only For Linux , because network mode host only for linux)
```docker
version: "3"
services: 
  nps_client:
    image: mmfei/nps_client
    container_name: "nps_client"
    network_mode: "host"
    restart: always
    environment: 
      - NPC_SERVER_ADDR=xxxxxxxxx:8024
      - NPC_SERVER_VKEY=xxxxxxxxxx
    volumes:
      - "./build_client/conf/:/npc/conf/"
```

```bash
docker-compose -f  docker-compose.client.yml up -d 
```


### For Max / Windows . please download : [click here for download npc client release](https://github.com/ehang-io/nps/releases)
```bash
wget https://github.com/ehang-io/nps/releases/download/v0.26.7/linux_amd64_client.tar.gz;  # For Linux 64 bit
tar xvzf linux_amd64_client.tar.gz;
./npc -server=192.168.0.103:8024 -vkey=es9cf58dy5qv1t47 -type=tcp  #ip:port and vkey , please fetch them from your server.
```