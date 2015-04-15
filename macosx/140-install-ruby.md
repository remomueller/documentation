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
rvmsudo rvm requirements
```

### 141 Install Ruby using RVM

```
rvm install 2.2.2
```

Activate Ruby 2.2.2

```
rvm 2.2.2
```

**NOTE** You may need to create a gemset to switch to 2.2.2 if it failed during the install.

```
rvm 2.2.2 --create
```

Verify Ruby version

```
ruby -v
```

```console
ruby 2.2.2p95 (2015-04-13 revision 50295) [x86_64-darwin14]
```

Set default Ruby

```
rvm alias create default ruby-2.2.2
```

### 142 Update Ruby Gems

```
gem update --system
```

for a specific version of gem

```
gem update --system 2.2.2 --no-ri --no-rdoc
```

### Next Step

[150 - Install Rails](https://github.com/remomueller/documentation/tree/master/macosx/150-rails.md)
