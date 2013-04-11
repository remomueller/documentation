## 35 Installing MySQL on Windows 7

### 64bit Windows 7

Download the MySQL 5.5.20 Windows 7 64bit MSI
  http://blog.mmediasys.com/2011/07/07/installing-mysql-on-windows-7-x64-and-using-ruby-with-it/

  [mysql-5.5.20-winx64.msi](http://dev.mysql.com/downloads/mirror.php?id=405766)

### 32bit Windows 7

Download the MySQL 5.5.30 Windows 7 32bit MSI

  [mysql-5.5.30-win32.msi](http://dev.mysql.com/downloads/mirror.php?id=411874)


### For Both

Install MySQL MSI Windows 7 by running installer

Follow instructions on Website above for setting up mysql


Download the MySQL Connector 32bit NoInstall

  [mysql-connector-c-noinstall-6.0.2-win32.zip](http://dev.mysql.com/downloads/mirror.php?id=377978)

Extract to

  C:\mysql-connector-c-noinstall-6.0.2-win32\

In command prompt run

  gem install mysql2 --platform=ruby -- --with-mysql-lib="C:\mysql-connector-c-noinstall-6.0.2-win32\lib" --with-mysql-include="C:\mysql-connector-c-noinstall-6.0.2-win32\include" --with-mysql-dir="C:\mysql-connector-c-noinstall-6.0.2-win32"


Copy libmysql.dll to Ruby Installation Bin

  copy C:\mysql-connector-c-noinstall-6.0.2-win32\lib\libmysql.dll C:\Ruby200\bin\libmysql.dll


### Next Step

[40 - Install CoffeeScript](https://github.com/remomueller/documentation/tree/master/windows/40-coffeescript.md)
