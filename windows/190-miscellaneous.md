## 190 Miscellaneous

#### Install Windows Service on Windows 7 (64-bit)

Based on information from: http://unicornless.com/systems-administration/run-thin-as-windows-service
Installing as a service Windows 7 Instructions (modified from www.dixis.com/?p=140):
Download and Install Windows Server 2003 Resource Kit Tools

  [Windows Server 2003 Resource Kit Tools - rktools.exe](http://www.microsoft.com/en-us/download/details.aspx?id=17657)

#### Running Server without Windows Service

```
rails s -e production
```

or

```
thin start -p 3000 -e production
```



### 191 Bcrypt-Ruby Error

If you get the warning `cannot load such file -- 2.0/bcrypt_ext` when running `bundle exec rake`, then you need to reinstall bcrypt-ruby

```
gem uninstall bcrypt

gem install bcrypt --platform=ruby --no-ri --no-rdoc
```


### 192 MySQL Gem Error

If you get the warning `cannot load such file -- mysql2/2.0/mysql2` when running `bundle exec rake` or `thin start`, then you need to reinstall mysql2

```
gem uninstall mysql2

# Make sure you select "All versions", especially if you have `mysql2-x.x.x-x86-mingw32` and `mysql2-x.x.x` gems installed!
```

Then reinstall as per the directions in [135 - Install MySQL](https://github.com/remomueller/documentation/blob/master/windows/135-mysql.md)
