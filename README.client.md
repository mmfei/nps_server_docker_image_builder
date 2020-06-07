# nps client

## docker run
```
docker run -d mmfei/nps_client -v ./build_client/conf:/npc/conf;
```

## docker compose
### docker-compose.client.yml
```docker
version: "3"
services: 
  nps_client:
    image: mmfei/nps_client
    container_name: "nps_client"
    # network_mode: "host"
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