## 130 Install Ruby Version Manager

Ruby Version Manager allows multiple instances of Ruby to exist.  This greatly aids upgrading to newer versions of Ruby without breaking existing Ruby installations.


### 131 Curl needs a new cacert.pem file to work correctly

NOTE: Not necessary on macOS


### 132 Multi-User install for RVM

```
cd ~/code/source
\curl -L https://get.rvm.io | sudo bash -s stable
```

**Important! Logout and login again to reload bash shell!**

Go to System Preferences -> Users & Groups

Select `rvm` under Groups and add your user to the RVM group by selecting the checkbox next to your user name.

Append the following to `~/.zshrc` if it didn't get added automatically:

```
[[ -s "/usr/local/rvm/scripts/rvm" ]] && . "/usr/local/rvm/scripts/rvm"
```

Create (or append to) `~/.bash_profile` file the following lines:

```
export rvmsudo_secure_path=0

# Add port bin to path to include yarn and node (Node.js)
export PATH="$PATH:/opt/local/bin"
```

Verify RVM version

Type `rvm --version`

```console
rvm 1.29.7 (latest)
```

In case rvm is not recognized, add the following to the bottom of `/etc/profile`

```
test -f /etc/profile.d/rvm.sh && source /etc/profile.d/rvm.sh
```

Install RVM Dependencies

Type `rvm requirements`, may require `rvmsudo rvm requirements`

RVM may also require `rvm group add rvm $USER` in order to set proper user permissions

Make sure you have the latest version of XCode installed. See [100 - Prerequisites](https://github.com/remomueller/documentation/blob/master/macos/100-prerequisites.md) for XCode installation instructions.


### 139 Upgrading Ruby Version Manager (optional)

If you already have RVM installed, you can use the following steps to upgrade RVM.

```
rvmsudo rvm get stable

rvm reload

sudo /opt/local/bin/port selfupdate

sudo /opt/local/bin/port outdated

sudo /opt/local/bin/port upgrade outdated

rvmsudo rvm requirements
```

**Note:** If you run into issues during the requirements installation, make sure you installed [MacPorts](https://github.com/remomueller/documentation/blob/master/macos/100-prerequisites.md#104-macports-for-best-integration-with-rvm) as a prerequisite and then switch to MacPorts by default: `rvm autolibs macports`

### Next Step

[140 - Install Ruby](https://github.com/remomueller/documentation/blob/master/macos/140-install-ruby.md)

