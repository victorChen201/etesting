## Install Hexo

```bash
sudo apt-get install nodejs-legacy npm
sudo npm install -g hexo-cli
```

## Clone website

```bash
git clone https://github.com/jarsonfang/etesting.git
cd etesting && git submodule init && git submodule update
```

## Install node_modules

```bash
cd etesting && npm install
```

## Preview on localhost

```bash
hexo s
```

## Generate and deploy

```bash
hexo clean
hexo d -g
```
