## 120 Install Git

Git is required for checking out projects from version control.

```
sudo yum -y install zlib-devel openssl-devel cpio expat-devel gettext-devel gcc perl-ExtUtils-MakeMaker
```

Install from source

```
cd ~/code/source
wget http://git-core.googlecode.com/files/git-1.7.10.tar.gz
tar xvzf git-1.7.10.tar.gz
rm git-1.7.10.tar.gz
cd git-*
./configure
make
sudo make install
```

Verify Git version by typing

```
git --version
```

Should return:

```console
git version 1.7.10
```

### Next Step

[130 - Install Ruby Version Manager](https://github.com/remomueller/documentation/tree/master/centos/130-install-rvm.md)