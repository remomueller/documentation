## 140 Install Ruby

Prerequisite: To compile Ruby 2.0.0-p247, Mac OS X 10.8.3+ and RVM 1.20.12+ are required.

To update rvm:

```
\curl -L https://get.rvm.io | sudo bash -s stable

or

rvm get stable
```

Install requirements

```
rvm requirements
```

### 141 Install Ruby using RVM

```
rvm install 2.0.0-p247
```

Activate Ruby 2.0.0-p247

```
rvm 2.0.0-p247
```

Verify Ruby version

```
ruby -v
```

```console
ruby 2.0.0p247 (2013-06-27 revision 41674) [x86_64-darwin12.4.0]
```

Set default Ruby

```
rvm alias create default ruby-2.0.0-p247
```

### 142 Update Ruby Gems

```
gem update --system
```

### Next Step

[150 - Install Rails](https://github.com/remomueller/documentation/tree/master/macosx/150-rails.md)
