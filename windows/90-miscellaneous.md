## 90 Miscellaneous

#### Install Windows Service on Windows 7 (64-bit)

Based on information from: http://unicornless.com/systems-administration/run-thin-as-windows-service
Installing as a service Windows 7 Instructions (modified from www.dixis.com/?p=140):
Download and Install Windows Server 2003 Resource Kit Tools

  [Windows Server 2003 Resource Kit Tools - rktools.exe](http://www.microsoft.com/en-us/download/details.aspx?id=17657)

#### Running Server without Windows Service

```console
rails s -e production
```

or

```console
thin start -p 3000 -e production
```



### 91 Bcrypt-Ruby Error

If you get the warning `cannot load such file -- 2.0/bcrypt_ext` when running `bundle exec rake`, then you need to reinstall bcrypt-ruby

```console
gem uninstall bcrypt-ruby

gem install bcrypt-ruby --platform=ruby --no-ri --no-rdoc
```

