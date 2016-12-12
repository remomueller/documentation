## 180 Install Node.js and CoffeeScript JavaScript compiler

Tools required by server to compile CoffeeScript files into JavaScript

### 181 Node.js and Node Package Manager

Download and compile node.js and Node Package Manager

```
cd ~/code/source
curl http://nodejs.org/dist/v0.10.13/node-v0.10.13.tar.gz | tar xvz
cd node-*
./configure
make
sudo make install
```

Verify Node.js installed by typing `which node` which should return:

```console
/usr/local/bin/node
```

Verify Node.js version by typing `node -v` which should return:

```console
v0.10.13
```

Verify npm installed by typing `which npm` which should return:

```console
/usr/local/bin/npm
```

Verify npm version by typing `npm -v` which should return:

```console
1.3.2
```

Make symbolic links for node and npm

```
sudo ln -s /usr/local/bin/node /usr/bin/node
sudo ln -s /usr/local/bin/npm /usr/bin/npm
```

### 182 CoffeeScript

Download and compile CoffeeScript

```
sudo npm install -g coffee-script
```

Verify CoffeeScript installed by typing `which coffee` which should return:

```console
/usr/local/bin/coffee
```

Make symbolic links for coffee

```
sudo ln -s /usr/local/bin/coffee /usr/bin/coffee
```

Verify CoffeeScript version by typing `coffee -v` which should return:

```console
CoffeeScript version 1.10.0
```

### Next Step

[190 - Install Rails Applications](https://github.com/remomueller/documentation/tree/master/centos/190-install-rails-applications.md)
