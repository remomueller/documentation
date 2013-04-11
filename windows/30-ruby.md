## 30 Installing Ruby and DevKit on Windows 7


### 64bit Windows 7

Download Ruby 2.0.0-p0 from http://rubyinstaller.org/downloads/

  http://rubyforge.org/frs/download.php/76806/rubyinstaller-2.0.0-p0-x64.exe

Download DevKit 4.7.2 from http://rubyinstaller.org/downloads/

  http://rubyforge.org/frs/download.php/76808/DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe


### 32bit Windows 7

Download Ruby 2.0.0-p0 from http://rubyinstaller.org/downloads/

  http://rubyforge.org/frs/download.php/76804/rubyinstaller-2.0.0-p0.exe

Download DevKit 4.7.2 from http://rubyinstaller.org/downloads/

  http://rubyforge.org/frs/download.php/76805/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe


### For Both

Install RubyInstaller and select

  Add Ruby to Path

  Associate .rb and .rbw files with Ruby

Open Command Prompt and UPDATE RUBY GEMS and BUNDLER

```console
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

```console
cd C:\DevKit

ruby dk.rb init

ruby dk.rb install
```

To test installation

```console
gem install rdiscount --platform=ruby
```

You should see `Temporarily enhancing PATH to include DevKit`, type the following to confirm the gem works

```console
ruby -rubygems -e "require 'rdiscount'; puts RDiscount.new('**Hello RubyInstaller**').to_html"
```

### Next Step

[35 - Install MySQL](https://github.com/remomueller/documentation/tree/master/windows/35-mysql.md)
