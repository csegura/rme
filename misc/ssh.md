# SSH related

ssh-copy-id windows -> linux

```
cat ~/.ssh/id_rsa.pub | ssh root@agora "cat >> ~/.ssh/authorized_keys"
```

github

```
ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-keygen -t rsa -b 4096 -C "your_email@example.com" (old)
```

ssh-agent

```
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```` 

add key to agent

```
ssh-add ~/.ssh/id_ed25519 
```

