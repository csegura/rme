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

github config ~/.ssh/config

```
Host github.com
      Hostname github.com
      PreferredAuthentications publickey
      IdentityFile ~/.ssh/gh
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

Windows ssh-agent

```
Set-Service ssh-agent -StartupType Manual
Start-Service ssh-agent
```
