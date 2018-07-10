## Install JDK
```shell
sudo apt-get install open-jdk
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-amd64
```
## Install Maven
```shell
wget http://mirrors.tuna.tsinghua.edu.cn/apache/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.tar.gz
tar xzfv apache-maven-3.5.2-bin.tar.gz
cd apache-maven-3.5.2/bin
export PATH=$PATH:`pwd`
vim conf/settings.xml
<localRepository>/path/to/local/repo</localRepository> ## The path direction connector project root dir
```
##  Checkout Code

```shell
git clone git@github.com:tjworks/daas.git
cd daas
```

## Build
```shell
export DAAS=development
./build
```