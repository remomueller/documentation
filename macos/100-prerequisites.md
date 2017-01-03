## 100 Prerequisites
Instructions for running on your macOS box.
Most recently tested on Apple macOS Sierra 10.12

Click Apple Logo in top left of screen and click **About This Mac**

```
macOS Sierra
Version 10.12
Proccessor 3.7 GHz Quad-Core Intel Xeon E5
Memory 12GB 1866 MHz DDR3 ECC
```

### 101 Log in using SSH or Putty
If you are logging into a remote Mac, use the following command from the terminal.

```
ssh user@railspro01
```

### 102 Create a Source Folder

```
mkdir ~/code
mkdir ~/code/source
```

### 103 XCode

Make sure you have the latest version of XCode installed. XCode 8.0 or greater for Sierra, XCode 6.1.1 or greater for Yosemite, XCode 4.6.3 or greater for Mountain Lion.

[developer.apple.com/xcode](https://developer.apple.com/xcode)

#### El Capitan/Sierra - Install Command Line Tools

Open Terminal and type:

```
xcode-select --install
```

#### Mountain Lion - Install Command Line Tools

Open XCode, go to `Preferences`, then select `Downloads`, and `Install Command Line Tools`.

### 104 MacPorts for best Integration with RVM

While Homebrew is a suitable alternative, this guide works best with MacPorts installed for RVM. This guide recommends the use of MacPorts and will not provide solutions for errors encountered due to using Homebrew.

Install MacPorts here:

https://www.macports.org/install.php

Choose the `.pkg` file for your OS, launch the package installer and follow the instructions provided by the installer.

After running the installer, create a symbolic link to the `port` command:

```
sudo ln -s /opt/local/bin/port /usr/local/bin/port
```

### Next Step

[110 - Startup](https://github.com/remomueller/documentation/tree/master/macos/110-startup.md)
