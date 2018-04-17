# All-In-One

## Install Go

```shell
wget https://dl.google.com/go/go1.10.linux-amd64.tar.gz
tar xzfv go1.10.linux-amd64.tar.gz -C $yourPath
mkdir -p ~/gopkg/
export GOPATH=~/gopkg/
export PATH=$PATH:$yourPath/bin/:$GOPATH/bin
```

## Install node-prune

```shell
go get github.com/tj/node-prune/cmd/node-prune
```

## Checkout

```shell
git clone git@github.com:tjworks/daas.git
cd daas
```

## Build

```shell
export DAAS_BUILD_NUMBER=0.0.15i
./build.sh
```

## 设置需要导出的软件版本

如果使用build步骤的版本号，可以省略这个步骤

```shell
export DAAS_BUILD_NUMBER=0.0.15i
```

>这里的软件版本号为docker镜像的tag，使用docker images可查看软件版本号，如果没有找到可用镜像，请先执行build脚本


## 导出所需文件并上传到服务器

```shell
./export-executable-file.sh
```

> 以上步骤都是在本地构建

## 递交启动脚本给用户

```shell
./tapdate.sh
```
>递交方式可以是电子邮件或者其它方式