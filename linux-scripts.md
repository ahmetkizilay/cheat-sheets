# ubuntu scripts

### Creating ssh key pair
```
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa
```

#### User management

List all users
```
cut -d: -f1 /etc/passwd
```

Create a user

```
sudo adduser <user>
```

Add user to a group
```
sudo usermod -aG <group> <user>
```

Make user a super user
```
gpasswd -a <user> sudo
```

List groups of a user
```
groups <user>
```
