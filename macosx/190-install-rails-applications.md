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

### 193 Install individual Ruby on Rails Applications

- [Hybrid](https://github.com/sleepepi/hybrid)
  - Sleep Portal code base
- [Review](https://github.com/remomueller/review)
  - CHAT Publications code base
- [Screen](https://github.com/remomueller/screen)
  - Screening application for clinical trials
- [Task Tracker](https://github.com/remomueller/tasktracker)
  - Task Tracker project management code base

### Next Step

[199 - Miscellaneous](https://github.com/remomueller/documentation/tree/master/macosx/199-miscellaneous.md)
