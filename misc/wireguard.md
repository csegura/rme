# Wireguard client

```sh
sudo apt install -y wireguard-tools resolvconf

# check /etc/resolv.conf
# edit /etc/wireguard/wg0.conf with dsired configuration

wg-quick up wg0
[#] ip link add wg0 type wireguard
[#] wg setconf wg0 /dev/fd/63
[#] ip -4 address add 10.1.1.2 dev wg0
[#] ip link set mtu 1420 up dev wg0
[#] resolvconf -a tun.wg0 -m 0 -x
[#] ip -4 route add 192.168.11.0/24 dev wg0
[#] ip -4 route add 172.19.55.0/24 dev wg0
 
sudo wg show
interface: wg0
  public key: fUltzMLG6BwrkbLfPyTDmt+uyzfBQphQTxyT/l6ybws=
  private key: (hidden)
  listening port: 51820

peer: eXLnxlefukamfpjxWERB7KZVYb7KXsnge7/xqhoGG1w=
  preshared key: (hidden)
  endpoint: 46.24.14.122:51820
  allowed ips: 172.19.55.0/24, 192.168.11.0/24
  latest handshake: 5 minutes, 11 seconds ago
  transfer: 476 B received, 564 B sent

ip addr show wg0
26: wg0: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none 
    inet 10.1.1.2/32 scope global wg0
       valid_lft forever preferred_lft forever
       
```

# Wireguard compose 

```yaml
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

```sh
scp root@agora:~/wireguard/peer1/peer1.png .

# Client configuration file
cat /config/peer1/peer1.conf
```
