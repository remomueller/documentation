## 175 Configuring Automatic Startup for Nginx

Important: Make sure the following setting is deselected!

  System Preferences => Sharing => Web Sharing (unchecked)

Otherwise the default Apache install will use port 80 instead of Nginx.

Based on: http://hunterford.me/nginx-startup-script-for-mac-os-x

```
sudo vi /Library/LaunchDaemons/org.nginx.nginx.plist
```

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>nginx</string>
    <key>Program</key>
    <string>/usr/local/nginx/sbin/nginx</string>
    <key>KeepAlive</key>
    <true/>
    <key>NetworkState</key>
    <true/>
    <key>LaunchOnlyOnce</key>
    <true/>
</dict>
</plist>
```

### Grant correct startup permissions

```
sudo chown root:wheel /Library/LaunchDaemons/org.nginx.nginx.plist
```

### Mark Nginx Service for Automatic startup

```
sudo launchctl load /Library/LaunchDaemons/org.nginx.nginx.plist
sudo launchctl start org.nginx.nginx
```

### Next Step

[179 - Nginx Commands](https://github.com/remomueller/documentation/tree/master/macos/179-nginx-commands.md)

[180 - Install CoffeeScript](https://github.com/remomueller/documentation/tree/master/macos/180-coffeescript.md)

