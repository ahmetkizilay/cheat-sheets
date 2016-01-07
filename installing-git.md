# Installing Git from source

Assuming that you have setup an Ubuntu server as shown [here](ubuntu-setup.md)

Install necessary programs
```sh
sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext \
 libz-dev libssl-dev autoconf
```
Visit [Git releases page](https://github.com/git/git/releases) and find the archive for the version you want to install.

```sh
wget https://github.com/git/git/archive/v2.7.0.tar.gz
```
Build commands
```sh
tar -zxf git-v2.7.0.tar.gz
cd git-v2.7.0
make configure
./configure --prefix=/usr
make all
sudo make install
```

See [this page](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for more info.
