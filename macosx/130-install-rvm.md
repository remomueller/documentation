## 130 Install Ruby Version Manager

Ruby Version Manager allows multiple instances of Ruby to exist.  This greatly aids upgrading to newer versions of Ruby without breaking existing Ruby installations.


### 131 Curl needs a new cacert.pem file to work correctly

NOTE: Not necessary on Mac OS X


### 132 Multi-User install for RVM

```
cd ~/code/source
\curl -L https://get.rvm.io | sudo bash -s stable
```

**Important! Logout and login again to reload bash shell!**

Verify RVM version

Type `rvm --version`

```console
rvm 1.25.25 (stable)
```

Install RVM Dependencies

Type `rvm requirements`, may require `rvmsudo rvm requirements`

RVM may also require `rvm group add rvm $USER` in order to set proper user permissions

Make sure you have the latest version of XCode installed. See [100 - Prerequisites](https://github.com/remomueller/documentation/tree/master/macosx/100-prerequisites.md) for XCode installation instructions.


### 139 Upgrading Ruby Version Manager (optional)

If you already have RVM installed, you can use the following steps to upgrade RVM.

```
[rvmsudo] rvm get stable

rvm reload

[rvmsudo] rvm requirements
```

### Next Step

[140 - Install Ruby](https://github.com/remomueller/documentation/tree/master/macosx/140-install-ruby.md)

