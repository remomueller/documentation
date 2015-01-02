## 150 Install Rails and Bundler

```
gem install bundler rails --no-ri --no-rdoc
```

If you run into this error:

```console
ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
    SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed (https://rubygems.global.ssl.fastly.net/quick/Marshal.4.8/bundler-1.7.10.gemspec.rz)
```

You may need to update **all** of the certificates using rvm.

**Check Status**

```
rvm osx-ssl-certs status all
```

```console
Certificates for /etc/openssl/cert.pem: Old.
Certificates for /usr/local/etc/openssl/cert.pem: Up to date.
```

**Update Certificates**

```
rvm osx-ssl-certs update all
```

### Next Step

[160 - Install Passenger](https://github.com/remomueller/documentation/tree/master/macosx/160-passenger.md)
