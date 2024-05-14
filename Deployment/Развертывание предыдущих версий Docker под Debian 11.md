---
tags:
- docker
- deployment
---
## Install specific Docker version
```
root@ptai421-agent-l:~# apt-cache madison docker-ce
 docker-ce | 5:23.0.0-1~debian.11~bullseye | https://download.docker.com/linux/debian bullseye/stable amd64 Packages
 docker-ce | 5:20.10.23~3-0~debian-bullseye | https://download.docker.com/linux/debian bullseye/stable amd64 Packages
 docker-ce | 5:20.10.22~3-0~debian-bullseye | https://download.docker.com/linux/debian bullseye/stable amd64 Packages
...
croot@ptai421-agent-l:~# apt-get install -y docker-ce=5:20.10.23~3-0~debian-bullseye docker-ce-cli=5:20.10.23~3-0~debian-bullseye containerd.io=1.6.15-1 docker-compose-plugin=2.15.1-1~debian.11~bullseye
```