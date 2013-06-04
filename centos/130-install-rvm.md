## 130 Installing Ruby using Ruby Version Manager

Ruby Version Manager allows multiple instances of Ruby to exist.  This greatly aids upgrading to newer versions of Ruby without breaking existing Ruby installations.

### 131 Curl needs a new cacert.pem file to work correctly (CentOS 5.7 only)

```
cd ~/code/source
mkdir curl-cacert
cd curl-cacert
wget http://curl.haxx.se/ca/cacert.pem
sudo cp /etc/pki/tls/certs/ca-bundle.crt /etc/pki/tls/certs/ca-bundle.crt.old
cat cacert.pem /etc/pki/tls/certs/ca-bundle.crt >> ca-bundle-new.crt
sudo cp ca-bundle-new.crt /etc/pki/tls/certs/ca-bundle.crt
```

### 132 Multi-User install for RVM

```
cd ~/code/source
\curl -L https://get.rvm.io | sudo bash -s stable

sudo vi /etc/group
```

Find the group rvm at the bottom and add the appropriate users to the group, ex: `user1` and `user2` to rvm group

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

```console
rvm 1.20.13 (stable)
```

Install RVM Dependencies (discover by typing: `rvm requirements`)

**NOTE: For centos >= 5.4 iconv-devel is provided by glibc**

Check which version of CentOS using:

```
cat /etc/redhat-release
```

For CentOS < 5.4

```
sudo yum install -y gcc-c++ patch readline readline-devel zlib zlib-devel libyaml-devel libffi-devel openssl-devel make bzip2 autoconf automake libtool bison iconv-devel
```

For CentOS >= 5.4, used this command for *railspro01*

```
sudo yum install -y gcc-c++ patch readline readline-devel zlib zlib-devel libyaml-devel libffi-devel openssl-devel make bzip2 autoconf automake libtool bison glibc
```

**NOTE:** If you get `warning: rpmts_HdrFromFdno: Header V3 RSA/SHA256 Signature, key ID 0608b895: NOKEY` when running, then sign your RPM and rerun yum install above

```
sudo rpm --import https://fedoraproject.org/static/0608B895.txt
sudo rpm --import http://packages.atrpms.net/RPM-GPG-KEY.atrpms
```

### 139 Upgrading Existing RVM (optional)

```
rvm get stable

rvm reload
```

### Next Step

[140 - Install Ruby](https://github.com/remomueller/documentation/tree/master/centos/140-install-ruby.md)
