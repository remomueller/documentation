## 199 Errors and Solutions

Note: Most issues are solved by [Removing Old Ruby Installations](https://github.com/remomueller/documentation/blob/master/windows/191-removing-old-rubies.md) and [Reinstalling Ruby](https://github.com/remomueller/documentation/blob/master/windows/130-ruby.md).

This page will help you identify WHAT the cause of the issue may be, but most solutions recommend a clean reinstall of Ruby.

### Command Prompt "Not Recognized as an Internal or External Command"

```
'ruby' is not recognized as an internal or external command, operable program or batch file.
'gem' is not recognized as an internal or external command, operable program or batch file.
'nsrr' is not recognized as an internal or external command, operable program or batch file.
```

If you receive one of the above messages when attempting to run Ruby or a Ruby gem, it means that Ruby was not added to the Windows path during the RubyInstaller installation wizard. This issue can be resolved by [Removing Old Ruby Installations](https://github.com/remomueller/documentation/blob/master/windows/191-removing-old-rubies.md) and [Reinstalling Ruby](https://github.com/remomueller/documentation/blob/master/windows/130-ruby.md) and particularly making sure to select **"Add Ruby to Path"** when the installer prompts you to check a series of checkmarks.


### Command Prompt "Undefined Method activate_bin_path" when launching a gem 

```
'<main>': undefined method 'activate_bin_path' for Gem:Module (NoMethodError)
```

If you receive the above message, it's highly likely that you are running an older version of RubyGems (the `gem` command).

If you type in `gem -v` and get a version that is `2.4.8` or lower, you will have to update RubyGems.

First try:

```
gem update --system
```

If this doesn't work (due to the SSL issue listed below), you may need to manually update the RubyGems command using [The Official Instructions](http://guides.rubygems.org/ssl-certificate-update/#installing-using-update-packages).

If the guide fails you, it may be easiest to [Removing All Ruby Installations](https://github.com/remomueller/documentation/blob/master/windows/191-removing-old-rubies.md) and [Reinstall Ruby](https://github.com/remomueller/documentation/blob/master/windows/130-ruby.md).


### OpenSSL Errors when installing gem on Windows

```
Unable to download data from https://rubygems.org/ - SSL_connect returned=1 errno=0 state=error: certificate verify failed (https://api.rubygems.org/specs.4.8.gz)
```

If you receive the above line after running a `gem install ___` command, this indicates that you are using an older version of RubyGems that no longer has updated certificates in order to access the newer RubyGems API.

You *may* be able to update the gem command using [the official guide](http://guides.rubygems.org/ssl-certificate-update/#installing-using-update-packages), however if this fails, [Remove All Ruby Installations](https://github.com/remomueller/documentation/blob/master/windows/191-removing-old-rubies.md) and [Reinstall Ruby](https://github.com/remomueller/documentation/blob/master/windows/130-ruby.md).


### "No Implicit Conversion of nil into String" error while running a gem command

```
ERROR:  While executing gem ... (TypeError)

   no implicit conversion of nil into String
```

If you run into the above command it may indicate that you have multiple version of Ruby installed on Windows, or that a newer installation partially overwrote an older installation. Multiple versions of Ruby cause issues, and in this case, [Remove All Ruby Installations](https://github.com/remomueller/documentation/blob/master/windows/191-removing-old-rubies.md) and [Reinstall Ruby](https://github.com/remomueller/documentation/blob/master/windows/130-ruby.md).
