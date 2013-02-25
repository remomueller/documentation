## 140 Install Ruby

Prerequisite: LibYAML may need to be installed, see [Pitfall 960](https://github.com/sleepepi/sleepepi/tree/master/virtual-machines/900-pitfalls.rdoc#960-ruby-missing-psych-libyaml)

  rvm pkg install libyaml

### 141 Install Ruby using RVM

  CC=/usr/bin/clang rvm install 2.0.0-p0 --with-libyaml-dir=/usr/local/rvm/usr

Activate Ruby 2.0.0-p0

  rvm 2.0.0-p0

Verify Ruby version

  ruby -v

  ruby 1.9.3p327 (2012-11-10 revision 37606) [x86_64-linux]

Set default Ruby

  rvm alias create default ruby-2.0.0-p0

### 142 Update Ruby Gems

  gem update --system

### Next Step

[50 - Install Rails](https://github.com/remomueller/documentation/tree/master/macosx/50-rails.rdoc)
