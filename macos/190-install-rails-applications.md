## 190 Install Ruby on Rails Applications

### 191 Initialize Production Directory and Permissions

```
cd /usr/local
sudo mkdir production
sudo chgrp rvm production
sudo chmod 775 production
```

### 192 Installing MySQL Library to allow compilation of mysql2 ruby gem

Install the MySQL version appropriate for you.
HIGHLY recommend using 5.1 and NOT 5.5, as 5.5 needs to be relinked everytime the mysql2 gem is reinstalled.

  http://www.mysql.com/downloads/mysql/5.1.html#downloads

Select `Mac OS X ver. 10.6 (x86, 64-bit), DMG Archive`

  mysql-5.1.61-osx10.6-x86_64.dmg

In case you need to install the `mysql` ruby gem, the following can be used

```
ARCHFLAGS="-arch x86_64" gem install mysql -- --with-mysql-config=/usr/local/mysql/bin/mysql_config
```

### 193 Install individual Ruby on Rails Applications

- [Sleep Portal](https://github.com/sleepepi/sleepportal)
  - Sleep Portal code base
- [Review](https://github.com/remomueller/review)
  - CHAT Publications code base
- [Screen](https://github.com/remomueller/screen)
  - Screening application for clinical trials
- [Task Tracker](https://github.com/remomueller/tasktracker)
  - Task Tracker project management code base

### Next Step

[199 - Miscellaneous](https://github.com/remomueller/documentation/blob/master/macos/199-miscellaneous.md)
