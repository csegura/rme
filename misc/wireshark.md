# Wireshark compose 

```
wireguard:
    image: lscr.io/linuxserver/wireguard:latest
    container_name: wireguard
    cap_add:
      - NET_ADMIN
      - SYS_MODULE
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Madrid
      - SERVERURL= #optional
      - SERVERPORT=51820 #optional
      - PEERS=1 #optional
      - PEERDNS=auto #optional
      - INTERNAL_SUBNET=10.1.1.0 #optional
      - ALLOWEDIPS=0.0.0.0/0 #optional
      - LOG_CONFS=true #optional
    volumes:
      - /root/wireguard:/config
      - /lib/modules:/lib/modules
    ports:
      - 51820:51820/udp
    sysctls:
      - net.ipv4.conf.all.src_valid_mark=1
    restart: unless-stopped
```

## copy peer1.png
```
scp root@agora:~/wireguard/peer1/peer1.png .
```