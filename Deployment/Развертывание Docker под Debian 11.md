---
origin:
  - https://docs.docker.com/engine/install/debian/
tags:
  - docker
  - deployment
  - x509
---
В данной инструкции описывается развертывание последней версии Docker. При необходимости развертывания предыдущих версий Docker необходимо воспользоваться [другой инструкцией](Развертывание%20предыдущих%20версий%20Docker%20под%20Debian%2011.md).
# Set up the repository
Update the apt package index and install packages to allow apt to use a repository over HTTPS:
```
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
Add Docker’s official GPG key:
```
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
Use the following command to set up the repository:
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
# Install Docker Engine
Update the apt package index:
```
sudo apt-get update
```
Install Docker Engine, containerd, and Docker Compose.
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
Verify that the Docker Engine installation is successful by running the hello-world image:
```
sudo docker run --rm hello-world
```
# Конфигурирование CA-сертификатов
Для того, чтобы получить возможность подключения к репозиториям, использующим пользовательские сертификаты, необходимо скопировать цепочку сертификатов в 
`/etc/docker/certs.d/dockerhub.ptdemo.local.org[:443]/ca.crt`