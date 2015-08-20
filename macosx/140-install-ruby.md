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

**Note:** If you run into issues during the requirements installation, make sure you installed [MacPorts](https://github.com/remomueller/documentation/blob/master/macosx/100-prerequisites.md#104-macports-for-best-integration-with-rvm) as a prerequisite and then switch to MacPorts by default: `rvm autolibs macports`

### 141 Install Ruby using RVM

```
rvm install 2.2.3
```

Activate Ruby 2.2.3

```
rvm 2.2.3
```

**NOTE** You may need to create a gemset to switch to 2.2.3 if it failed during the install.

```
rvm 2.2.3 --create
```

Verify Ruby version

```
ruby -v
```

```console
ruby 2.2.3p173 (2015-08-18 revision 51636) [x86_64-darwin15]
```

Set default Ruby

```
rvm alias create default ruby-2.2.3
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
