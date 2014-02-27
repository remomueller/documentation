## 170 Install Nginx

These instructions detail a simple installation of nginx. If you want to include an additional security module, or wish to use an alternative version of nginx, you can follow the instructions provided in [171 - Install Nginx With Extra Modules](https://github.com/remomueller/documentation/tree/master/macosx/171-install-nginx-with-extra-modules.md) instead.

### Start the Passenger installer

```
rvmsudo passenger-install-nginx-module
```

Type `<enter>`

```
Which languages are you interested in?

Use <space> to select.

 ‣ ⬢  Ruby
   ⬡  Python
   ⬡  Node.js
   ⬡  Meteor
```

Deselect Python and Node.js using the `<space>` then type `<enter>`

```
1. Yes: download, compile and install Nginx for me. (recommended)

Enter your choice (1 or 2) or press Ctrl-C to abort:
```

Type `1`

```
Where do you want to install Nginx to?

Please specify a prefix directory [/opt/nginx]:
```

Type `/usr/local/nginx`


### Next Step

[173 - Nginx Configuration](https://github.com/remomueller/documentation/blob/master/macosx/173-nginx-configuration.md)



