# Setup

```
sudo apt install docker.io
```

To create the docker group and add your user:

Add your user to the docker group.
```
sudo usermod -aG docker ${USER}
```
You would need to loog out and log back in so that your group membership is re-evaluated or type the following command:
```
su -s ${USER}
```
Verify that you can run docker commands without sudo.
