## 171 Install Nginx with Extra Modules

This document describes how to install nginx with extra modules in case the simple approach outlined in [170 - Install Nginx](https://github.com/remomueller/documentation/tree/master/macosx/170-install-nginx.md) is not sufficient.

Specifically, `headers-more-nginx-module` will be installed in order to remove server and x-powered-by headers for better security using `more_clear_headers`.

[SPDY](http://en.wikipedia.org/wiki/SPDY) will be installed in order to compress HTTP headers and decrease web page load.


### Compiling OpenSSL 1.0.1+ requirement for SPDY

Install openssl 1.0.1.e on Mac

```
cd ~/code/source
wget -O openssl.tar.gz http://www.openssl.org/source/openssl-1.0.1e.tar.gz
tar xvzf openssl.tar.gz
rm openssl.tar.gz
cd openssl-1.0.1e
./Configure darwin64-x86_64-cc --prefix=/usr/local no-threads shared
make
sudo make install
```

### Download nginx source code

```
cd /tmp
mkdir nginxplus
cd /tmp/nginxplus

wget -O nginx.tar.gz http://www.nginx.org/download/nginx-1.4.6.tar.gz
tar xzvf nginx.tar.gz
rm nginx.tar.gz

wget -O headers-more-nginx-module.tar.gz https://github.com/agentzh/headers-more-nginx-module/archive/v0.20.tar.gz --no-check-certificate
tar xzvf headers-more-nginx-module.tar.gz
rm headers-more-nginx-module.tar.gz
```

### Start the Passenger Installer

```
rvmsudo passenger-install-nginx-module
```

Type `<enter>`

```
Which languages are you interested in?

Use <space> to select.

 ‣ ⬢  Ruby
   ⬡  Python
   ⬡  Node.js
   ⬡  Meteor
```

Deselect Python and Node.js using the `<space>` then type `<enter>`

```console
2. No: I want to customize my Nginx installation. (for advanced users)

Enter your choice (1 or 2) or press Ctrl-C to abort:
```

Type `2`

```console
Where is your Nginx source code located?

Please specify the directory:
```

Type `/tmp/nginxplus/nginx-1.4.6`

```console
Where do you want to install Nginx to?

Please specify a prefix directory [/opt/nginx]:
```

Type `/usr/local/nginx`

```console
Extra Nginx configure options

If you want to pass extra arguments to the Nginx 'configure' script, then
please specify them. If not, then specify nothing and press Enter.

If you specify nothing then the 'configure' script will be run as follows:

  sh ./configure ...

Extra arguments to pass to configure script:
```

Type
```
--with-http_spdy_module --with-cc-opt=-I/usr/local/include --with-ld-opt=-L/usr/local/lib --add-module=/tmp/nginxplus/headers-more-nginx-module-0.20
```

```console
Confirm configure flags

The Nginx configure script will be run as follows:

  sh ./configure ...

Is this what you want? (yes/no) [default=yes]:
```

Type `<enter>`


### Next Step

[173 - Nginx Configuration](https://github.com/remomueller/documentation/blob/master/macosx/173-nginx-configuration.md)
