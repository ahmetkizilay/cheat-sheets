# Setting up NodeJS

Assuming that you have setup an Ubuntu server as shown [here](ubuntu-setup.md)


#### Installing Node.JS
Download a recent version of NodeJS
```sh
wget https://nodejs.org/dist/v4.2.3/node-v4.2.3-linux-x64.tar.gz
```

Extract the archive into node folder
```sh
mkdir node
tar xvf node-v*.tar.gz --strip-components=1 -C ./node
```

Configure npm
```sh
mkdir node/etc
echo 'prefix=/usr/local' > node/etc/npmrc
```

Create symbolic links
```sh
sudo mv node /opt/
sudo chown -R root: /opt/node

sudo ln -s /opt/node/bin/node /usr/local/bin/node
sudo ln -s /opt/node/bin/npm /usr/local/bin/npm
```

[Based on](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-14-04)
#### Setting up pm2

Install pm2 globally
```sh
sudo npm install pm2 -g
```

To start you app with pm2
```sh
pm2 start <index.js>
```

See [pm2 github repo](https://github.com/Unitech/pm2) for more info.
