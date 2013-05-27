## 140 Install Ruby

Prerequisite: To compile Ruby 2.0.0-p0, Mac OS X 10.8.3+ and RVM 1.8.21+ are required.

To update rvm:

```
curl -L get.rvm.io | bash -s head

or

rvm get head
```

### 141 Install Ruby using RVM

```
rvm install 2.0.0 --autolibs=3 --verify-downloads 1
```

Activate Ruby 2.0.0-p0

```
rvm 2.0.0-p0
```

Verify Ruby version

```
ruby -v
```

```console
ruby 2.0.0p0 (2013-02-24 revision 39474) [x86_64-darwin12.2.0]
```

Set default Ruby

```
rvm alias create default ruby-2.0.0-p0
```

### 142 Update Ruby Gems

```
gem update --system
```

### Next Step

[150 - Install Rails](https://github.com/remomueller/documentation/tree/master/macosx/150-rails.md)
