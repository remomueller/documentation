## 100 Prerequisites
Instructions for running on your Mac OS X box.
Tested on Apple Mountain Lion 10.8.4 and Apple Mavericks 10.9

Click Apple Logo in top left of screen and click **About This Mac**

```
Mac OS X
Version 10.9
Proccessor 2.5 GHz Intel Core i5
Memory 4GB 1333 MHz DDR3
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

Make sure you have the latest version of XCode installed. XCode 5.0.2 or greater for Mavericks, XCode 4.6.3 or greater for Mountain Lion

[developer.apple.com/xcode](https://developer.apple.com/xcode)

#### Mavericks - Install Command Line Tools

Open Terminal and type:

```
xcode-select --install
```

#### Mountain Lion - Install Command Line Tools

Open XCode, go to `Preferences`, then select `Downloads`, and `Install Command Line Tools`.


### Next Step

[110 - Startup](https://github.com/remomueller/documentation/tree/master/macosx/110-startup.md)
