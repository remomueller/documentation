### 170 Install Phusion Passenger (Web server), used on *railspro01*

**Apache**: Compile Apache Passenger module

```
rvmsudo passenger-install-apache2-module
```

**Nginx**: Compile Nginx Passenger module

```
rvmsudo passenger-install-nginx-module
```

`<enter>`

```console
1. Yes: download, compile and install Nginx for me. (recommended)

Enter your choice (1 or 2) or press Ctrl-C to abort:
```

Type `1`

```console
Where do you want to install Nginx to?

Please specify a prefix directory [/opt/nginx]:
```

Type `/usr/local/nginx`


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

### Next Step

[180 - Install CoffeeScript](https://github.com/remomueller/documentation/tree/master/centos/180-coffeescript.md)
