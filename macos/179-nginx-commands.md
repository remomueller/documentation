## 179 Nginx Commands

### Manual Nginx Start Stop Restart

start

```
sudo /usr/local/nginx/sbin/nginx
```

stop

```
sudo /usr/local/nginx/sbin/nginx -s stop
```

stop alternative (graceful)

```
kill -QUIT $( cat /usr/local/nginx/logs/nginx.pid )
```

restart

```
kill -HUP $( cat /usr/local/nginx/logs/nginx.pid )
```

### Next Step

[180 - Install CoffeeScript](https://github.com/remomueller/documentation/tree/master/macos/180-coffeescript.md)
