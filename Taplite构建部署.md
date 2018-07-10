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


## 导出所需的文件

```shell
./lite/export-executable-file-lite.sh
```

## 启动
```
cd taplite-data
./taplite.sh
```

> 如需运行任务，请手动向数据库中导入数据