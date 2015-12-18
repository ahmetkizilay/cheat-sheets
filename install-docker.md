# Setting up Docker

### Installing Docker
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

### Installing docker-compose
Visit the [releases](https://github.com/docker/compose/releases) page for docker-compose on Github.

Depending on the version you would like to install, run:
```
sudo su
curl -L https://github.com/docker/compose/releases/download/1.5.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```
Visit [here](https://docs.docker.com/compose/install/) for more info.

### Sample Scripts
#### Sample Dockerfile.

```
FROM node:4.2
MAINTAINER Ahmet Kizilay <ahmet.kizilay@gmail.com>
COPY package.json /src/package.json
RUN cd /src; npm install

COPY . /src

EXPOSE 3000

WORKDIR /src
CMD ["npm", "start"]
```
For caching, it is important to copy `package.json` or `Gemfile` and installing dependencies before copying the entire application.

#### Build an image
Assuming the dockerfile is in the current directory
```
# dont forget the dot
docker build -t ahmetkizilay/app .
```
#### Create and start container
```
docker --rm run ahmetkizilay/app npm run test:coverage
```
`--rm` option removes the container once it is done.

#### Sample docker-compose file
Starts a container with neo4j, and links it to the web app.
```
db:
  image: neo4j/neo4j
  environment:
    - NEO4J_AUTH=none
  cap_add:
    - SYS_RESOURCE
web:
  build: .
  command: /bin/bash run-tests.sh
  ports:
    - "3000:3000"
  links:
    - db
```
#### Polling DB for startup
You need to check if your db is ready before running your command.
```
#!/bin/bash

while [ $(curl -s -o /dev/null -w "%{http_code}" $DB_PORT_7474_TCP_ADDR:7474) -ne 200 ]; do
    sleep 2
done

rake testing:rails["http://$DB_PORT_7474_TCP_ADDR:7474"]

```
#### Start neo4j
With authentication disabled. Visit the [official repo](https://hub.docker.com/r/neo4j/neo4j/) for more options.
```
docker run \
    --detach \
    --publish=7474:7474 \
    --volume=$HOME/neo4j/data:/data \
    --ulimit=nofile=40000:40000
    --env=NEO4J_AUTH=none
    neo4j/neo4j
```
