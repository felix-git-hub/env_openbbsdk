# openbb platform sdk

full functional openbb platform with jupyter lab support;

docker pull ghcr.io/felix-git-hub/openbb_docker:latest


Feature
1. based on debian bookworm, integraded with openbb sdk
2. /config is mounted with normal user, otherwise jupyter may be not able to adjust font size
3. upgraded from openbb sdk[3.x] to openbb platfrom[4.x]

## reference
https://docs.openbb.co/platform/installation
https://github.com/OpenBB-finance/OpenBBTerminal/tree/develop/examples

## how to create docker
docker-compose.yml
```
---
version: "2.1"
services:
  openbb:
    image: ghcr.io/felix-git-hub/openbb_docker:latest
    container_name: openbb
    environment:
      - TZ=Asia/Shanghai
      - PUID=1000
      - PGID=1001
      - CONFIG_FILE=/config/.jupyter/jupyter_lab_config.py #optional
    volumes:
      - /folder/to/data:/config
    restart: unless-stopped
    
    network_mode: bridge
    ports:
      - 8888:8888
```

## how to use the openbb terminal
docker exec -it --user abc openbb bash
