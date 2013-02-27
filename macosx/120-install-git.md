## 120 Install Git

Git is required for checking out projects from version control. Mac usually has git preinstalled, you can check if it exists by typing:

```console
git --version
```

```
git version 1.7.10
```

Install from source

```console
cd ~/code/source
wget http://git-core.googlecode.com/files/git-1.7.10.tar.gz
tar xvzf git-1.7.10.tar.gz
rm git-1.7.10.tar.gz
cd git-*
./configure
make
sudo make install
```

Verify Git version by typing `git --version` which should return

```
git version 1.7.10
```

### Next Step

[130 - Install Ruby Version Manager](https://github.com/remomueller/documentation/tree/master/macosx/130-install-rvm.md)
