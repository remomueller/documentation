## 140 Install Ruby

Make sure you followed [100 - Prerequisites](https://github.com/remomueller/documentation/tree/master/macosx/100-prerequisites.md) to successfully install Ruby

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
rvm install 2.1.2
```

Activate Ruby 2.1.2

```
rvm 2.1.2
```

Verify Ruby version

```
ruby -v
```

```console
ruby 2.1.2p95 (2014-05-08 revision 45877) [x86_64-darwin13.0]
```

Set default Ruby

```
rvm alias create default ruby-2.1.2
```

### 142 Update Ruby Gems

```
gem update --system
```

### Next Step

[150 - Install Rails](https://github.com/remomueller/documentation/tree/master/macosx/150-rails.md)
