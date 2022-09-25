
Enable homes

```
romheat@CSSNAS:/etc$ sudo synogroup --add docker
Group Name: [docker]
Group Type: [AUTH_LOCAL]
Group ID:   [65536]
Group Members: 
romheat@CSSNAS:/etc$ sudo synogroup --member docker romheat,root
Group Name: [docker]
Group Type: [AUTH_LOCAL]
Group ID:   [65536]
Group Members: 
0:[romheat]
1:[root]
romheat@CSSNAS:/etc$ sudo synogroup --member docker root
Group Name: [docker]
Group Type: [AUTH_LOCAL]
Group ID:   [65536]
Group Members: 
0:[root]
romheat@CSSNAS:/etc$ sudo chown root:docker /var/run/docker.sock

sudo synopkg restart Docker

```
