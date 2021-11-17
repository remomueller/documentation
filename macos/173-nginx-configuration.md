## 173 Nginx Configuration

Edit `sudo vi /usr/local/nginx/conf/nginx.conf`

```
http {
  passenger_root /usr/local/rvm/gems/ruby-3.1.0-preview1/gems/passenger-6.0.12;
  passenger_ruby /usr/local/rvm/gems/ruby-3.1.0-preview1/wrappers/ruby;

  # Disable anonymous telemetry reporting.
  passenger_disable_anonymous_telemetry off;

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
  # # Stop server from announcing additional headers, only available with extra module installed!
  # # https://github.com/remomueller/documentation/blob/master/macos/171-install-nginx-with-extra-modules.md
  # more_clear_headers 'Server';
  # more_clear_headers 'X-Powered-By';
  # more_clear_headers 'X-Runtime';

  server {
    listen      80;
    server_name _;
    rewrite     ^(.*)   https://MYDOMAIN.COM$1 permanent;
  }

  server {
    listen      443 ssl;

    server_name _;

    ssl_certificate      cert.pem;
    ssl_certificate_key  cert.key;

    ssl_session_timeout  5m;

    ssl_protocols TLSv1.1 TLSv1.2; # TLSv1.3;
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

### Next Step

[175 - Nginx Automatic Startup](https://github.com/remomueller/documentation/blob/master/macos/175-nginx-automatic-startup-configuration.md)
