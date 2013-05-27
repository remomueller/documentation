## 130 Install Ruby Version Manager

Ruby Version Manager allows multiple instances of Ruby to exist.  This greatly aids upgrading to newer versions of Ruby without breaking existing Ruby installations.

### 131 Curl needs a new cacert.pem file to work correctly

NOTE: Not necessary on Mac OS X

### 132 Multi-User install for RVM

```
cd ~/code/source
sudo bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer )

sudo vi /etc/group
```

Find the group rvm at the bottom and add the appropriate users to the group, ex: user1 and user2 to rvm group

Changed from:

```
rvm:x:20001:
```

To

```
rvm:x:20001:user1,user2
```

**Important! Logout and login again to reload bash shell!**

Verify RVM version by typing `rvm --version` which should return

```
rvm 1.18.14 (stable)
```

Install RVM Dependencies (discover by typing: `rvm requirements`)

Make sure you have the latest version of XCode installed. XCode 4.3.1 or greater for Lion

[developer.apple.com/xcode](https://developer.apple.com/xcode)


### 139 Upgrading Ruby Version Manager (optional)

If you already have RVM installed, you can use the following steps to upgrade RVM.

```
rvmsudo rvm get stable

rvm reload
```

### Next Step

[140 - Install Ruby](https://github.com/remomueller/documentation/tree/master/macosx/140-install-ruby.md)

