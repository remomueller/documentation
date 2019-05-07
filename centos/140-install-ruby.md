## 140 Install Ruby

Prerequisite: Install may require certain requirements to be installed

```
rvmsudo rvm requirements
```

### 141 Install Ruby using RVM

```
rvm install 2.6.3
```

Activate Ruby 2.6.3

```
rvm 2.6.3
```

Verify Ruby version

```
ruby -v
```

```console
ruby 2.6.3p62 (2019-04-16 revision 67580) [x86_64-linux]
```

Set default Ruby

```
rvm alias create default ruby-2.6.3
```

### 142 Update Ruby Gems

```
gem update --system --no-document
```

### Next Step

You have successfully installed Ruby on CentOS. If you have been directed here from installation instructions for the NSRR gem, Edfize, or Spout, you can now return to continue the gem installation instructions.

- Back to [NSRR Gem Installation](https://github.com/nsrr/nsrr-gem#installation)
- Back to [Edfize Gem Installation](https://github.com/sleepepi/edfize#installation)
- Back to [Spout Gem Installation](https://github.com/sleepepi/spout#installation)

For those installing the entire Rails stack, continue below.

[150 - Install Rails](https://github.com/remomueller/documentation/blob/master/centos/150-install-rails.md)
