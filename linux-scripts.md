# ubuntu scripts

### Creating ssh key pair
```
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa
```

### User management

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

#### Server Monitoring
Summary of disk usage
```
df -h --total
```
Summary of all processes
```
top
```
Free memory
```
free -m
```

#### Searching files
Search for a string in a file
```
grep -e <term> <file>
```
Print how many times the term appears
```
grep -e <term> <file> --count
```

#### Extract Tar archives
Extract all files in archive
```
tar -zxvf backup.tar.gz -C /target/directory
```
List files in archive
```
tar -tvf backup.tar.gz
```
Print only the top level item
```
tar -tf backup.tar.gz | sed -e 's@/.*@@' | uniq
```

#### Check available package version on apt
```
apt-cache madison <package-name>
```
