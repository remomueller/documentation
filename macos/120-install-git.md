## 120 Install Git

Git is required for checking out projects from version control. Mac usually has git preinstalled, you can check if it exists by typing:

```
git --version
```

```console
git version 1.7.10
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

[130 - Install Ruby Version Manager](https://github.com/remomueller/documentation/blob/master/macos/130-install-rvm.md)
