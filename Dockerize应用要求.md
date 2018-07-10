## 使用容器名或者主机名来代替应用程序中所使用的IP地址
** example **
下面是Docker部署容器的配置文件
```yaml
version: "3"
services:
  web:
    image: web
    hostname: web
    ports:
      - "3000:3000"
  mongo:
    image: mongo:3.2.10
    hostname: mongo 
    ports:
      - "27017:27017"
    volumes:
      - ./mongoData:/data/db
```
此时应用程序需要连接到MongoDB应该使用MongoDB的主机名
```js
const MongoClient = require('mongodb').MongoClient
const server = require('server')
const { get, post } = server.router
const config = require('config')
console.info(config)
let url = 'mongodb://mongo:27017/test' //使用mongo:27017代替，此处mongo是用mongo容器的主机名
server([
  get('/', async ctx => {
    try {
      let db = await MongoClient.connect(url)
      let adminDb = db.admin()
      console.info(config)
      let dbs = await adminDb.listDatabases()
      return dbs
    } catch (e) {
      return e.message
    }
  })
])
```
## 对于MongoDB，请使用使用现有的MongoDB复制集
```
mongodb://bjb.mongoing.com:27017,bjd.mongoing.com:27017,lax.mongoing.com:27017/beidou?replicaSet=rs
```
> 请注意该URI已经指定连接到beidou数据库，注意更改