## Require
[Docker](https://docs.docker.com/)



## Setup

### Yarn
````
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```
### Node.js
```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
```
### MongoDB

```
### Mongodb
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
```
### Docker
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
### update and install

```
sudo apt-get update
sudo apt install yarn nodejs nginx mongodb-org docker-ce 
```

```
sudo usermod -aG docker $USER
mkdir -p /etc/docker/
echo '{"registry-mirrors": ["https://0bbqupb9.mirror.aliyuncs.com"]}' > /etc/docker/daemon.json
sudo service docker restart
docker swarm init 
```

## Checkout
> Notice: 如果不是master分支，clone后注意检出需要构建的分支

```
git clone https://beidoubot:beidoub0t@github.dongcha.io/tjworks/daas.git
cd daas/demo
docker-compose up -d mysql oracle
cd ..
```
## Set Environment Variables 
```shell
export DAAS_BUILD_NUMBER=1.0.0 MONGO_PORT=27017 BACKEND_PORT=3030 FRONTEND_PORT=8083  STACK_NAME=xxxx  TAPDATA_ENV=production
```
## TAPDATA_ENV
- production 生产环境
- uat            用户测试环境
- dev           开发环境

>STACK_NAME 如果不设置将会随机生成，当TAPDATA_ENV的值为production时或者为空时，部署时将会询问超级管理员的用户名与密码，如果留空或者没有填写用户名密码将会使用user: admin@admin.com  password: admin 作为超级管理员密码

## Build

```shell
./build.sh
```

## Depoly

```
./depoly.sh
```