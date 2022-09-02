# nvidia-container-toolkit

https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html

```
[ /etc ]# cat lsb-release
DISTRIB_ID="VMware Photon OS"
DISTRIB_RELEASE="4.0"
DISTRIB_CODENAME=Photon
DISTRIB_DESCRIPTION="VMware Photon OS 4.0"
[ /etc ]# tdnf -y install yum
[using capability match for 'yum']
[using capability match for 'yum']
Package yum is already installed.
Nothing to do.
```

## Installation

```
[ ~/tmp ]# distribution=rhel9.0
[ ~/tmp ]# curl -s -L https://nvidia.github.io/libnvidia-container/$distribution/libnvidia-container.repo |  tee /etc/yum.repos.d/nvidia-container-toolkit.repo
[libnvidia-container]
name=libnvidia-container
baseurl=https://nvidia.github.io/libnvidia-container/stable/centos8/$basearch
repo_gpgcheck=1
gpgcheck=0
enabled=1
gpgkey=https://nvidia.github.io/libnvidia-container/gpgkey
sslverify=1
sslcacert=/etc/pki/tls/certs/ca-bundle.crt

[libnvidia-container-experimental]
name=libnvidia-container-experimental
baseurl=https://nvidia.github.io/libnvidia-container/experimental/centos8/$basearch
repo_gpgcheck=1
gpgcheck=0
enabled=0
gpgkey=https://nvidia.github.io/libnvidia-container/gpgkey
sslverify=1
sslcacert=/etc/pki/tls/certs/ca-bundle.crt

[ ~/tmp ]# yum install nvidia-container-toolkit
Refreshing metadata for: 'libnvidia-container'
libnvidia-container                      46866 100%
Installing:
libnvidia-container1               x86_64            1.10.0-1                libnvidia-container   3.06M 3206547
libnvidia-container-tools          x86_64            1.10.0-1                libnvidia-container 101.01k 103435
nvidia-container-toolkit           x86_64            1.10.0-1                libnvidia-container   8.75M 9172248

Total installed size:  11.90M 12482230
Is this ok [y/N]: y

Downloading:
libnvidia-container1                   1032872 100%
libnvidia-container-tools                54192 100%
nvidia-container-toolkit               3209432 100%
Testing transaction
Running transaction
Installing/Updating: libnvidia-container1-1.10.0-1.x86_64
Installing/Updating: libnvidia-container-tools-1.10.0-1.x86_64
Installing/Updating: nvidia-container-toolkit-1.10.0-1.x86_64

Complete!
```


```
docker run --rm --gpus all nvidia/cuda:11.4.0-base-ubuntu20.04 nvidia-smi
Unable to find image 'nvidia/cuda:11.4.0-base-ubuntu20.04' locally
11.4.0-base-ubuntu20.04: Pulling from nvidia/cuda
d5fd17ec1767: Already exists
e19a6dde28b7: Pull complete
794922120b42: Pull complete
91a55f6b0796: Pull complete
6089b86cf2a6: Pull complete
Digest: sha256:d85036f4e7796bbd0329f6e900c0ec9f91a5c226688877e06aa64ba5b54b601d
Status: Downloaded newer image for nvidia/cuda:11.4.0-base-ubuntu20.04
Fri Sep  2 10:02:59 2022
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.57.02    Driver Version: 470.57.02    CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:1B:00.0 Off |                  N/A |
|  0%   61C    P0     1W / 200W |      0MiB /  7982MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```
