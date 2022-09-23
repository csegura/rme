# Procedure

To relocate the Docker root directory, complete the following steps as root or a user with “sudo all” authority:

Stop the Docker services:

```
sudo -i

systemctl stop docker
systemctl stop docker.socket
systemctl stop containerd
```

Create the necessary directory structure into which to move Docker root by running the following command. This directory structure must reside on a file system with at least 50 GB free disk space. Significantly more disk space might be required depending on your daily ingestion volumes and data retention policy.

```
mkdir -p /data
```

Move Docker root to the new directory structure:

```sudo mv /var/lib/docker /data```

Edit the file /etc/docker/daemon.json. If the file does not exist, create the file by running the following command:

```
sudo vim /etc/docker/daemon.json
```

Add the following information to this file:

```
{
  "data-root": "/data/docker"
}
```

After the /etc/docker/daemon.json file is saved and closed, restart the Docker services:

```
sudo systemctl start docker
```

After you run the command, all Docker services through dependency management will restart.
Validate the new Docker root location:

```
docker info -f '{{ .DockerRootDir}}'
```
