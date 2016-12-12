## 140 Install Ruby

Prerequisite: Install may require certain requirements to be installed

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
ruby 2.0.0p247 (2013-06-27 revision 41674) [x86_64-linux]
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

You have successfully installed Ruby on Windows. If you have been directed here from installation instructions for the NSRR gem, Edfize, or Spout, you can now return to continue the gem installation instructions.

- Back to [NSRR Gem Installation](https://github.com/nsrr/nsrr-gem#installation)
- Back to [Edfize Gem Installation](https://github.com/sleepepi/edfize#installation)
- Back to [Spout Gem Installation](https://github.com/sleepepi/spout#installation)

For those installing the entire Rails stack, continue below.

[150 - Install Rails](https://github.com/remomueller/documentation/tree/master/centos/150-install-rails.md)
