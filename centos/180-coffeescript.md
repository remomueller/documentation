## 180 Install Node.js and CoffeeScript JavaScript compiler

Tools required by server to compile CoffeeScript files into JavaScript

### 181 Node.js and Node Package Manager

Download and compile node.js and Node Package Manager

```
cd ~/code/source
curl -L https://nodejs.org/dist/v6.10.2/node-v6.10.2.tar.gz | tar xvz
cd node-v6.10.2/
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
v6.10.2
```

Verify npm installed by typing `which npm` which should return:

```console
/usr/local/bin/npm
```

Verify npm version by typing `npm -v` which should return:

```console
3.10.10
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
CoffeeScript version 1.12.5
```

### Next Step

[190 - Install Rails Applications](https://github.com/remomueller/documentation/blob/master/centos/190-install-rails-applications.md)
