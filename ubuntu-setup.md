# Setting up an ubuntu server

#### Add server ip to the host file
If your server does not have an domain name setup, add the ip address to your `/etc/hosts` file. now you have an easy way to remember the server address.

#### Creating a new user
Upon creating an image on Digital Ocean, AWS or somewhere else, create a new user in super user group

Create a new user and add to the sudo group
```
# create a user named huruc
adduser huruc
gpasswd -a huruc sudo
```

Copy your public key to the server to authenticate via ssh
```
ssh-copy-id -i ~/.ssh/id_rsa.pub huruc@SERVER-IP
```

Note: If you need to create a new key pair, follow the instructions [here](linux-scripts.md#creating-ssh-key-pair).

#### Disable root access
Disable root access through ssh by updating `/etc/ssh/sshd_config`. Add the following line:
```
vim /etc/ssh/sshd_config
# type `PermitRootLogin no`
service ssh restart
```

#### Run an update and install packages
Make sure to get the latest updates
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential curl
```
