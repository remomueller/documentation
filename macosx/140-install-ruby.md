## 140 Install Ruby

Prerequisite: To compile Ruby 2.0.0-p0, Mac OS X 10.8.3+ and RVM 1.8.21+ are required.

To update rvm:

```console
curl -L get.rvm.io | bash -s head

or

rvm get head
```

### 141 Install Ruby using RVM

```console
rvm install 2.0.0 --autolibs=3 --verify-downloads 1
```

Activate Ruby 2.0.0-p0

```console
rvm 2.0.0-p0
```

Verify Ruby version

```console
ruby -v
```

```
ruby 2.0.0p0 (2013-02-24 revision 39474) [x86_64-darwin12.2.0]
```

Set default Ruby

```console
rvm alias create default ruby-2.0.0-p0
```

### 142 Update Ruby Gems

```console
gem update --system
```

### Next Step

[50 - Install Rails](https://github.com/remomueller/documentation/tree/master/macosx/50-rails.rdoc)
