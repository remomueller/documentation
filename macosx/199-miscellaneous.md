## 199 Miscellaneous

### PostgreSQL PG Gem installation failure (and solution)

```
Installing pg (0.17.0)
Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

    /usr/local/rvm/rubies/ruby-2.1.0/bin/ruby extconf.rb
checking for pg_config... no
No pg_config... trying anyway. If building fails, please try again with
 --with-pg-config=/path/to/pg_config
checking for libpq-fe.h... no
Can't find the 'libpq-fe.h header
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.
```


If you get the above error while attempting to install the pg gem, then you may need to install pg manually:

```
gem install pg --no-ri --no-rdoc -- --with-pg-config="/Library/PostgreSQL/9.3/bin/pg_config"
```

Note that the location depends on which version of PostgreSQL you have installed. (The above is for the enterprisedb 9.3 install)

More detailed explanation here: http://stackoverflow.com/a/9669523/1611947

### Errors when compiling Passenger due to missing OpenSSL 1.0.1+ and other Mac Development Headers

If you try to install passenger and run into the following error, you may be missing the necessary openssl and pcre development headers headers

```
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: .libs/libpcre.a(libpcre_la-pcre_string_utils.o) has no symbols

/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: .libs/libpcre.a(libpcre_la-pcre_string_utils.o) has no symbols

r-5.0.20/buildout/common/libpassenger_common/Utils/CachedFileStat.o /usr/local/rvm/gems/ruby-2.2.3/gems/passenger-5.0.20/buildout/common/libpassenger_common/UnionStationFilterSupport.o /usr/local/rvm/gems/ruby-2.2.3/gems/passenger-5.0.20/buildout/common/libboost_oxt.a -lstdc++ -lpthread -lm /tmp/passenger.e3zmx0/pcre-8.34/.libs/libpcre.a -lssl -lcrypto -lz

Undefined symbols for architecture x86_64:

  "_SSL_CTX_set_next_protos_advertised_cb", referenced from:

      _ngx_http_ssl_merge_srv_conf in ngx_http_ssl_module.o

ld: symbol(s) not found for architecture x86_64

clang: error: linker command failed with exit code 1 (use -v to see invocation)

make[1]: *** [objs/nginx] Error 1

make: *** [build] Error 2
```


If you are missing PCRE:
```
sudo port install pcre
```

If you are missing OpenSSL
```
cd ~/code/source
curl -L http://www.openssl.org/source/openssl-1.0.1q.tar.gz | tar xvz
cd openssl-1.0.1q
./Configure darwin64-x86_64-cc --prefix=/usr/local no-threads shared
make
sudo make install
```

### Updating SSL Certificates with MacPorts

Make sure you have OpenSSL installed:

```
openssl version
```

```
openssl version
sudo port sync
sudo port selfupdate
sudo port install
```

Check to make sure the version updated again.
```
openssl version
```

To update the certificate file:

```
cd /opt/local/etc/openssl
sudo curl -O http://curl.haxx.se/ca/cacert.pem
sudo mv cacert.pem cert.pem
```
