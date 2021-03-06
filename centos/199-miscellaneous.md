## 199 Miscellaneous

### Yum Install Issues

If you get `warning: rpmts_HdrFromFdno: Header V3 RSA/SHA256 Signature, key ID 0608b895: NOKEY` when running, then you need to update your GPG keys:

```
sudo rpm --import https://fedoraproject.org/static/0608B895.txt
sudo rpm --import http://packages.atrpms.net/RPM-GPG-KEY.atrpms
```

After this, running the `sudo yum install` should work correctly

### Checking and setting the hostname

*railspro01* had the wrong hostname, _localhost_, after being rebooted.

To check the hostname type:

```
hostname
```

Which should return:

```console
railsproXX.com
```

To set the hostname type:

```
sudo hostname railsproXX.com
```

If this does not work type:

```
sudo vi /etc/sysconfig/network
```

And change the line that says:

```
HOSTNAME=./set_hostname.sh: line 14: dialog: command not found
```

To

```
HOSTNAME=railsproXX.com
```


### Nginx startup on boot


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

### Automatic startup Nginx at Boot

From http://articles.slicehost.com/2009/2/2/centos-adding-an-nginx-init-script

`sudo vi /etc/init.d/nginx`

```
#!/bin/sh
#
# nginx - this script starts and stops the nginx daemin
#
# chkconfig:   - 85 15
# description:  Nginx is an HTTP(S) server, HTTP(S) reverse \
#               proxy and IMAP/POP3 proxy server
# processname: nginx
# config:      /usr/local/nginx/conf/nginx.conf
# pidfile:     /usr/local/nginx/logs/nginx.pid

# Source function library.
. /etc/rc.d/init.d/functions

# Source networking configuration.
. /etc/sysconfig/network

# Check that networking is up.
[ "$NETWORKING" = "no" ] && exit 0

nginx="/usr/local/nginx/sbin/nginx"
prog=$(basename $nginx)

NGINX_CONF_FILE="/usr/local/nginx/conf/nginx.conf"

lockfile=/var/lock/subsys/nginx

start() {
    [ -x $nginx ] || exit 5
    [ -f $NGINX_CONF_FILE ] || exit 6
    echo -n $"Starting $prog: "
    daemon $nginx -c $NGINX_CONF_FILE
    retval=$?
    echo
    [ $retval -eq 0 ] && touch $lockfile
    return $retval
}

stop() {
    echo -n $"Stopping $prog: "
    killproc $prog -QUIT
    retval=$?
    echo
    [ $retval -eq 0 ] && rm -f $lockfile
    return $retval
}

restart() {
    configtest || return $?
    stop
    start
}

reload() {
    configtest || return $?
    echo -n $"Reloading $prog: "
    killproc $nginx -HUP
    RETVAL=$?
    echo
}

force_reload() {
    restart
}

configtest() {
  $nginx -t -c $NGINX_CONF_FILE
}

rh_status() {
    status $prog
}

rh_status_q() {
    rh_status >/dev/null 2>&1
}

case "$1" in
    start)
        rh_status_q && exit 0
        $1
        ;;
    stop)
        rh_status_q || exit 0
        $1
        ;;
    restart|configtest)
        $1
        ;;
    reload)
        rh_status_q || exit 7
        $1
        ;;
    force-reload)
        force_reload
        ;;
    status)
        rh_status
        ;;
    condrestart|try-restart)
        rh_status_q || exit 0
            ;;
    *)
        echo $"Usage: $0 {start|stop|status|restart|condrestart|try-restart|reload|force-reload|configtest}"
        exit 2
esac
```

`sudo chmod +x /etc/init.d/nginx`

`sudo /sbin/chkconfig nginx on`

### Available nginx start and stop commands

```
sudo service nginx stop
sudo service nginx start
sudo service nginx restart
sudo service nginx status
sudo service nginx configtest
```
