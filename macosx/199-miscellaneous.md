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
