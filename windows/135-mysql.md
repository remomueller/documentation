## 135 Installing MySQL on Windows 7

### 64bit Windows 7

Download the MySQL 5.5.20 Windows 7 64bit MSI

Based on: [Installing MySQL On Windows 7 x64 and using Ruby With It](http://blog.mmediasys.com/2011/07/07/installing-mysql-on-windows-7-x64-and-using-ruby-with-it/)

Download: [mysql-5.5.20-winx64.msi](http://dev.mysql.com/downloads/mirror.php?id=405766)

### 32bit Windows 7

Download the MySQL 5.5.30 Windows 7 32bit MSI, [mysql-5.5.30-win32.msi](http://dev.mysql.com/downloads/mirror.php?id=411874)

### For Both

Install MySQL MSI Windows 7 by running installer

Follow instructions on Website above for setting up mysql


Download the MySQL Connector 32bit NoInstall, [mysql-connector-c-noinstall-6.0.2-win32.zip](http://dev.mysql.com/downloads/mirror.php?id=377978)


Extract to (32-bit) `C:\mysql-connector-c-noinstall-6.0.2-win32\`
Extract to (64-bit) `C:\mysql-connector-c-noinstall-6.0.2-winx64\`

In command prompt run (32 bit)

```
gem install mysql2 --platform=ruby -- --with-mysql-lib="C:\mysql-connector-c-noinstall-6.0.2-win32\lib" --with-mysql-include="C:\mysql-connector-c-noinstall-6.0.2-win32\include" --with-mysql-dir="C:\mysql-connector-c-noinstall-6.0.2-win32"
```

(64 bit)

```
gem install mysql2 --platform=ruby -- '--with-mysql-dir="C:\mysql-connector-c-noinstall-6.0.2-winx64"'
```

Copy libmysql.dll to Ruby Installation Bin (32-bit)

```
copy C:\mysql-connector-c-noinstall-6.0.2-win32\lib\libmysql.dll C:\Ruby200\bin\libmysql.dll
```

Copy libmysql.dll to Ruby Installation Bin (64-bit)

```
copy C:\mysql-connector-c-noinstall-6.0.2-winx64\lib\libmysql.dll C:\Ruby200-x64\bin\libmysql.dll
```

### Next Step

[140 - Install CoffeeScript](https://github.com/remomueller/documentation/blob/master/windows/140-coffeescript.md)
