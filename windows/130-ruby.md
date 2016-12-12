## 130 Installing Ruby and DevKit on Windows 7


### 64bit Windows 7

Download Ruby 2.3.3 from http://rubyinstaller.org/downloads/

  [Ruby 2.3.3 (x64)](https://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.3.3-x64.exe)

Download DevKit 4.7.2 from http://rubyinstaller.org/downloads/
                                
  [Development Kit 4.7.2 (x64)](https://dl.bintray.com/oneclick/rubyinstaller/DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe)

### 32bit Windows 7

Download Ruby 2.3.3 from http://rubyinstaller.org/downloads/

  [Ruby 2.3.3](https://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.3.3.exe)

Download DevKit 4.7.2 from http://rubyinstaller.org/downloads/

  [Development Kit 4.7.2](https://dl.bintray.com/oneclick/rubyinstaller/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe)


### For Both

Install RubyInstaller and select

- Add Ruby to Path

- Associate .rb and .rbw files with Ruby

Open Command Prompt and update Ruby Gem command and install Bundler

```
gem update --system --no-document

gem --version

  2.6.8    # Or greater!

gem install bundler --no-document

bundle --version

  Bundler version 1.13.6    # Or greater!
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
gem install rdiscount --platform=ruby --no-document
```

You should see `Temporarily enhancing PATH to include DevKit`, type the following to confirm the gem works

```
ruby -rubygems -e "require 'rdiscount'; puts RDiscount.new('**Hello RubyInstaller**').to_html"
```

### Next Step

You have successfully installed Ruby on Windows. If you have been directed here from installation instructions for the NSRR gem, Edfize, or Spout, you can now return to continue the gem installations instructions.

- Back to [NSRR Gem Installation](https://github.com/nsrr/nsrr-gem#installation)
- Back to [Edfize Gem Installation](https://github.com/sleepepi/edfize#installation)
- Back to [Spout Gem Installation](https://github.com/sleepepi/spout#installation)

For those installing the entire Rails stack, continue below.

[135 - Install MySQL](https://github.com/remomueller/documentation/tree/master/windows/135-mysql.md)
