## 140 Install Ruby

Make sure you followed [100 - Prerequisites](https://github.com/remomueller/documentation/blob/master/macos/100-prerequisites.md) to successfully install Ruby

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

**Note:** If you run into issues during the requirements installation, make sure you installed [MacPorts](https://github.com/remomueller/documentation/blob/master/macos/100-prerequisites.md#104-macports-for-best-integration-with-rvm) as a prerequisite and then switch to MacPorts by default: `rvm autolibs macports`

### 141 Install Ruby using RVM

```
rvm install ruby-3.1.0-preview1
```

Activate Ruby 3.1.0-preview1

```
rvm 3.1.0-preview1
```

Verify Ruby version

```
ruby -v
```

```console
ruby 3.1.0preview1 (2021-11-09 master 5a3b2e6141) [x86_64-darwin20]
```

Set default Ruby

```
rvm alias create default ruby-3.1.0-preview1
```

### 142 Update Ruby Gems

```
gem update --system --no-document
```

### Next Step

You have successfully installed Ruby on MacOS. If you have been directed here from installation instructions for the NSRR gem, Edfize, or Spout, you can now return to continue the gem installation instructions.

- Back to [NSRR Gem Installation](https://github.com/nsrr/nsrr-gem#installation)
- Back to [Edfize Gem Installation](https://github.com/sleepepi/edfize#installation)
- Back to [Spout Gem Installation](https://github.com/sleepepi/spout#installation)

For those installing the entire Rails stack, continue below.

[150 - Install Rails](https://github.com/remomueller/documentation/blob/master/macos/150-rails.md)
