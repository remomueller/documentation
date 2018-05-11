## 130 Installing Ruby and DevKit on Windows 7

**Important**: If you have an existing installation of Ruby, make sure you [completely remove the installation](https://github.com/remomueller/documentation/blob/master/windows/191-removing-old-rubies.md) before proceeding with the steps below. Check to see if you have `C:\DevKit` or `C:\Ruby*\` folders that may be previous installations Ruby on Windows.

If you run into any errors during this guide, check the [Errors and Solutions](https://github.com/remomueller/documentation/blob/master/windows/199-errors-and-solutions.md) for the causes.

### 64bit Windows 10

Download Ruby+Devkit 2.4.4-1 (x64) from https://rubyinstaller.org/downloads/

[Ruby+Devkit 2.4.4-1 (x64)](https://github.com/oneclick/rubyinstaller2/releases/download/rubyinstaller-2.4.4-1/rubyinstaller-devkit-2.4.4-1-x64.exe)

### 32bit Windows 10

Download Ruby+Devkit 2.4.4-1 (x86) from https://rubyinstaller.org/downloads/

[Ruby+Devkit 2.4.4-1 (x86)](https://github.com/oneclick/rubyinstaller2/releases/download/rubyinstaller-2.4.4-1/rubyinstaller-devkit-2.4.4-1-x86.exe)


### Run Ruby Installer

Double-click RubyInstaller and select:

- Check "I accept the License"
- Click Next

- Use default Ruby installation folder: `C:\Ruby24-x64` or `C:\Ruby24-x86`
- Check "Add Ruby executables to your PATH"
- Check "Associate .rb and .rbw files with this Ruby installation"
- Check "Use UTF-8 as default external encoding."
- Click Install

- Check "MSYS2 development toolchain"
- Click Next

- Check "Run 'ridk install' to setup MSYS2 and development toolchain."
- Click Finish

The installation may take around 5 to 10 minutes.

A RubyInstaller2 "cmd.exe" window will open up with choices.

**DO NOT ENTER A NUMBER. Simply click "ENTER".**
- Click ENTER

The installation may take an additional 5 to 10 minutes. At the end is should say MSYS2 installed successfully, you can ignore other errors.

- Close installer

### Update RubyGems and Install Bundler
Open Command Prompt and update RubyGems command and install Bundler

```
gem update --system --no-document 
# Allow access (check all options) if Windows Security Alert displays.

gem --version

  2.7.6    # Or greater!

gem install bundler --no-document
# Overwrite executable? Type "y" and hit Enter if this appears.

bundle --version

  Bundler version 1.16.1    # Or greater!
```

### Verify Installation (Optional)
Open Command Prompt

```
gem install rdiscount --platform=ruby --no-document
```

You should see `Temporarily enhancing PATH for MSYS/MINGW...`, type the following to confirm the gem works:

```
ruby -rubygems -e "require 'rdiscount'; puts RDiscount.new('**Hello RubyInstaller**').to_html"
```

It should output:

```
<p><strong>Hello RubyInstaller</strong></p>
```

### Next Step

You have successfully installed Ruby on Windows. If you have been directed here from installation instructions for the NSRR gem, Edfize, or Spout, you can now return to continue the gem installation instructions.

- Back to [NSRR Gem Installation](https://github.com/nsrr/nsrr-gem#installation)
- Back to [Edfize Gem Installation](https://github.com/sleepepi/edfize#installation)
- Back to [Spout Gem Installation](https://github.com/sleepepi/spout#installation)

For those installing the entire Rails stack, continue below.

[135 - Install MySQL](https://github.com/remomueller/documentation/blob/master/windows/135-mysql.md)
