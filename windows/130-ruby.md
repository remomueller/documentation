## 130 Installing Ruby and DevKit on Windows 7


### 64bit Windows 7

Download Ruby 2.0.0-p247 from http://rubyinstaller.org/downloads/

  [Ruby 2.0.0-p247 (x64)](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.0.0-p247-x64.exe?direct)

Download DevKit 4.7.2 from http://rubyinstaller.org/downloads/

  [Development Kit 4.7.2 (x64)](http://rubyforge.org/frs/download.php/76808/DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe)


### 32bit Windows 7

Download Ruby 2.0.0-p0 from http://rubyinstaller.org/downloads/

  [Ruby 2.0.0-p247](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.0.0-p247.exe?direct)

Download DevKit 4.7.2 from http://rubyinstaller.org/downloads/

  [Development Kit 4.7.2](http://rubyforge.org/frs/download.php/76805/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe)


### For Both

Install RubyInstaller and select

- Add Ruby to Path

- Associate .rb and .rbw files with Ruby

Open Command Prompt and UPDATE RUBY GEMS and BUNDLER

```
gem update --system

gem --version

  2.0.3    # Or greater!

gem install bundler --no-ri --no-rdoc

bundle --version

  Bundler version 1.3.5    # Or greater!
```


Follow instructions here to install DevKit

  https://github.com/oneclick/rubyinstaller/wiki/Development-Kit

Extract DevKit to `C:\DevKit` by double clicking the downloaded executable

Initialize and install DevKit

```
cd C:\DevKit

ruby dk.rb init

ruby dk.rb install
```

To test installation

```
gem install rdiscount --platform=ruby --no-ri --no-rdoc
```

You should see `Temporarily enhancing PATH to include DevKit`, type the following to confirm the gem works

```
ruby -rubygems -e "require 'rdiscount'; puts RDiscount.new('**Hello RubyInstaller**').to_html"
```

### Next Step

[135 - Install MySQL](https://github.com/remomueller/documentation/tree/master/windows/135-mysql.md)
