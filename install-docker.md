# install Docker

Add docker to trusted sources
```
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

sudo vim /etc/apt/sources.list.d/docker.list
# and insert (for Ubuntu 14.04)
# deb https://apt.dockerproject.org/repo ubuntu-trusty main

sudo apt-get update
```

Remove docker if it was installed before
```
# sudo apt-get purge lxc-docker
```

Install docker
```
sudo apt-get install docker-engine
```
Add your user to docker group
```
sudo usermod -aG docker <username>
# and relogin
```
start docker service
```
sudo service docker start
```
Visit [here](https://docs.docker.com/engine/installation/ubuntulinux/) for more info.

#### Installing docker-compose
Visit the [releases](https://github.com/docker/compose/releases) page for docker-compose on Github.

Depending on the version you would like to install, run:
```
sudo su
curl -L https://github.com/docker/compose/releases/download/1.5.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```
Visit [here](https://docs.docker.com/compose/install/) for more info.
