## 130 Installing Ruby using Ruby Version Manager

Ruby Version Manager allows multiple instances of Ruby to exist.  This greatly aids upgrading to newer versions of Ruby without breaking existing Ruby installations.

### 131 Curl needs a new cacert.pem file to work correctly (CentOS 5.7 only)

```console
cd ~/code/source
mkdir curl-cacert
cd curl-cacert
wget http://curl.haxx.se/ca/cacert.pem
sudo cp /etc/pki/tls/certs/ca-bundle.crt /etc/pki/tls/certs/ca-bundle.crt.old
cat cacert.pem /etc/pki/tls/certs/ca-bundle.crt >> ca-bundle-new.crt
sudo cp ca-bundle-new.crt /etc/pki/tls/certs/ca-bundle.crt
```

### 132 Multi-User install for RVM

```console
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

### 133 Install Ruby and Ruby Gems

```
rvm install 2.0.0-p195
```

Activate Ruby 2.0.0-p195

```
rvm 2.0.0-p195
```

Verify Ruby version

```
ruby -v
```

```console
ruby 2.0.0p195 (2013-05-14 revision 40734) [x86_64-linux]
```

Set default Ruby

```
rvm alias create default ruby-2.0.0-p195
```

Update Ruby Gems and install Bundler, Rails, and Passenger

```
gem update --system
gem install bundler rails passenger --no-ri --no-rdoc
```

### 134 Install Phusion Passenger (Web server), used on *railspro01*

```
sudo yum install httpd-devel apr-devel apr-util-devel curl-devel
passenger-install-apache2-module
```

Or, if you want to install the Nginx version instead:

```console
rvmsudo passenger-install-nginx-module
```

`<enter>`

```console
1. Yes: download, compile and install Nginx for me. (recommended)

Enter your choice (1 or 2) or press Ctrl-C to abort: 1

Please specify a prefix directory [/opt/nginx]: /usr/local/nginx
```

**Apache**: Edit `sudo vi /etc/httpd/conf.d/rails.conf`

```
LoadModule passenger_module /usr/local/rvm/gems/ruby-2.0.0-p195/gems/passenger-4.0.5/ext/apache2/mod_passenger.so
PassengerRoot /usr/local/rvm/gems/ruby-2.0.0-p195/gems/passenger-4.0.5
PassengerRuby /usr/local/rvm/wrappers/ruby-2.0.0-p195/ruby

PassengerMaxPoolSize 12
PassengerPoolIdleTime 3600

RackEnv production
PassengerHighPerformance on

<VirtualHost *:80>
  RewriteEngine On
  RewriteCond %{HTTPS} off
  RewriteRule (.*) https://www.example.com%{REQUEST_URI}
</VirtualHost>
```


**Nginx**: Edit `sudo vi /usr/local/nginx/conf/nginx.conf`

```
http {
  passenger_root /usr/local/rvm/gems/ruby-2.0.0-p195/gems/passenger-4.0.5;
  passenger_ruby /usr/local/rvm/wrappers/ruby-2.0.0-p195/ruby;

  # Allow for up to 10 megabyte uploads
  include       mime.types;
  default_type  application/octet-stream;
  client_max_body_size 10m;

  # Enable GZIP compression
  gzip on;
  gzip_http_version 1.0;
  gzip_vary on;
  gzip_comp_level 6;
  gzip_proxied any;
  gzip_types text/plain text/css application/json application/javascript application/x-javascript text/javascript;
  proxy_set_header Accept-Encoding  "";
  gzip_buffers 16 8k;
  # Disable gzip for certain browsers.
  gzip_disable "MSIE [1-6].(?!.*SV1)";

  # Stop server from announcing own details
  server_tokens off;

  server {
    listen      80;
    server_name _;
    rewrite     ^(.*)   https://www.example.com$1 permanent;
  }

  server {
    listen      443;
    server_name _;

    ssl                  on;
    ssl_certificate      cert.pem;
    ssl_certificate_key  cert.key;

    ssl_session_timeout  5m;

    ssl_protocols SSLv3 TLSv1 TLSv1.1 TLSv1.2;
    ssl_ciphers  HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers   on;

    # rack_env production; # This is the default, could be changed to development and uncommented.

    root  /var/www/html;   # <--- For rails app on subdomains
    passenger_enabled on;
    # Symbolic links in /var/www/html that point to the PUBLIC directory of the rails apps.
    # Ex: rails app at /usr/local/rails_app1
    # sudo ln -s /usr/local/rails_app1/public /var/www/html/rails_app1
    # passenger_base_uri /rails_app1;
    # passenger_base_uri /rails_app2;
  }
}
```

**Apache**: Restart web server

```
sudo service httpd restart
```

**Nginx**: Restart web server, http://wiki.nginx.org/CommandLine#Stopping_or_Restarting_Nginx

```
kill -HUP $( cat /usr/local/nginx/logs/nginx.pid )
```
