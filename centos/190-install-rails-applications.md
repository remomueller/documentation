## 190 Install Ruby on Rails Applications

### 191 Initialize Production Directory and Permissions

```
cd /usr/local
sudo mkdir production
sudo chgrp rvm production
sudo chmod 775 production
```

### 192 Installing MySQL Library to allow compilation of mysql2 ruby gem

```
sudo yum install mysql mysql-devel
```

### 193 Installing libraries to allow compilation of nokogiri gem

```
sudo yum install libxml libxml-devel libxslt libxslt-devel
```

### 194 Install individual Ruby on Rails Applications

- [Sleep Portal](https://github.com/sleepepi/sleepportal)
  - Sleep Portal code base
- [Review](https://github.com/remomueller/review)
  - CHAT Publications code base
- [Screen](https://github.com/remomueller/screen)
  - Screening application for clinical trials
- [Task Tracker](https://github.com/remomueller/tasktracker)
  - Task Tracker project management code base


### Next Step

[199 - Miscellaneous](https://github.com/remomueller/documentation/tree/master/centos/199-miscellaneous.md)
