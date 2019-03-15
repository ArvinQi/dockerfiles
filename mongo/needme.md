# Doc

## 启动后配置数据库1，2
``` bash
# 1
use admin
# 2
config = { "_id": "r1", "members": [{ "_id": 0, "host": "172.18.18.142:27019", "priority": 1 }, { "_id": 1, "host": "172.18.18.142:27018", "priority": 1 }, { "_id": 2, "host": "172.18.18.142:27016", "priority": 1 }] };
# 3
rs.initiate(config);
```


## connect to mongo
``` bash
    mongo mongodb://172.18.18.142:27019,172.18.18.142:27018,172.18.18.142:27016/admin?replicaSet="r1"
```