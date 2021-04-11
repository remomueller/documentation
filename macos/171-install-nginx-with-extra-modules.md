## 171 Install Nginx with Extra Modules

This document describes how to install nginx with extra modules in case the simple approach outlined in [170 - Install Nginx](https://github.com/remomueller/documentation/blob/master/macos/170-install-nginx.md) is not sufficient.

Specifically, `headers-more-nginx-module` will be installed in order to remove server and x-powered-by headers for better security using `more_clear_headers`.

**NOTE**
Passenger 5.0.28 does not compile correctly with Xcode 7.3. Make sure to switch to Xcode 7.2.1 when compiling otherwise nginx will fail to launch rails applications, giving the page "An error occurred. [...] Faithfully yours, nginx."

To switch, the following can be done (older version of [Xcode 7.2.1](https://developer.apple.com/services-account/download?path=/Developer_Tools/Xcode_7.2.1/Xcode_7.2.1.dmg) will need to be installed under a different name, i.e. `Xcode72.app`):

```
sudo xcode-select -switch /Applications/Xcode72.app/Contents/Developer
```

and to switch back when done using reinstalling the passenger gem and nginx:

```
sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer
```

The above steps can also be done through Xcode -> Preferences -> Locations:

![xcode 7.3 and 7.2.1](https://cloud.githubusercontent.com/assets/316479/14956437/c77494d0-104d-11e6-87f4-e38bdb055d5b.png)

### Download nginx source code

```
cd /tmp
mkdir nginxplus
cd /tmp/nginxplus
curl -L http://www.nginx.org/download/nginx-1.19.9.tar.gz | tar xvz
curl -L https://github.com/openresty/headers-more-nginx-module/archive/v0.33.tar.gz --insecure | tar xvz
```

### Start the Passenger Installer

```
rvmsudo passenger-install-nginx-module --auto --prefix=/usr/local/nginx --nginx-source-dir=/tmp/nginxplus/nginx-1.19.9 --extra-configure-flags="--add-module=/tmp/nginxplus/headers-more-nginx-module-0.33" --languages ruby
```

or manually

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

Type `/tmp/nginxplus/nginx-1.15.12`

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
--add-module=/tmp/nginxplus/headers-more-nginx-module-0.33
```

```console
Confirm configure flags

The Nginx configure script will be run as follows:

  sh ./configure ...

Is this what you want? (yes/no) [default=yes]:
```

Type `<enter>`


### Next Step

[173 - Nginx Configuration](https://github.com/remomueller/documentation/blob/master/macos/173-nginx-configuration.md)
