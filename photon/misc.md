# PHOTON MISC

### enable/disable docker
```
systemctl start docker
systemctl enable docker
```

### install packages
```
tdnf install git
tdnf install github-cli
tdnf install zsh
tdnf install wget
tdnf install docker-compose
tdnf install nfs-tools
tdnf install nfs-utils
```

### keyboard
```
localectl
localectl list-keymaps
tdnf install kbd
localectl list-keymaps
localectl set-keymap es
reboot
```

### sshd root access
```
cat > /etc/systemd/network/10-static-en.network << "EOF"
[Match]
Name=eth0
[Network]
Address=192.168.1.200/24
Gateway=192.168.1.1
```

```chmod 644 10-static-en.network```
 
### install portainer - expose port 9000
``` 
docker volume create portainer_data
ls -la
docker run -d -p 9000:9000 --name Portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```

### iptables - open docker expose ports
```
iptables -L  (list rules)
iptables -nL (show port numbers)
# open port 9000
iptables -I INPUT 4 -p tcp --dport 9000 -j ACCEPT
```
