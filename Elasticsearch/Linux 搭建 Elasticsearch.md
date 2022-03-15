# 下载和解压安装包

- 官网下载地址：[https://www.elastic.co/cn/downloads/elasticsearch](https://www.elastic.co/cn/downloads/elasticsearch)

  选择合适的版本下载，可以在 windows 下载后 上传到 linux。

  > 注意由于 es 和 jdk 是一个强依赖的关系，所以当我们在新版本的 es 压缩包中包含有自带的 jdk，但是当我们的 linux 中已经安装了 jdk 之后，就会发现启动 es 的时候优先去找的是 linux 中已经装好的 jdk，此时如果 jdk 的版本不一致，就会造成 jdk 不能正常运行 。具体 es 和 jdk 的对应版本参考：[https://www.elastic.co/cn/support/matrix#matrix_browsers](https://www.elastic.co/cn/support/matrix#matrix_browsers)

   也可以在Linux命令行，直接执行以下命令进行下载（下载比较慢）：

  ```sh
  wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.3.2-linux-x86_64.tar.gz
  ```

-  执行解压缩命令：

  ```sh
  tar -zxvf elasticsearch-7.3.2-linux-x86_64.tar.gz
  ```




# ES 入门

## 倒排索引

ES 是**面向文档型数据库**，一条数据在这里就是一个文档。 为了方便大家理解，我们将 ES 里存储文档数据和关系型数据库 MySQL 存储数据的概念进行一个类比:

<img src="Linux 搭建 Elasticsearch.assets/1646980507853.png" alt="1646980507853" style="zoom: 60%;" />

ES 里的 Index 可以看做一个库， Documents 则相当于表的行。



## 创建索引

对比关系型数据库，创建索引就等同于创建数据库。 

向 ES 服务器发送 PUT 请求：

```sh
# 后面接 jq 是将返回的 JSON 字符串格式化
curl -X PUT http://127.0.0.1:9200/shopping | jq
```

服务器返回响应：

```sh
{
    "acknowledged": true,//响应结果
    "shards_acknowledged": true,//分片结果
    "index": "shopping"//索引名称
}
```



## 查询和删除索引

### 查看所有索引

向 ES 服务器发送 GET 请求：

```sh
curl -X GET http://127.0.0.1:9200/_cat/indices?v
```

这里请求路径中的 _cat 表示查看的意思， indices 表示索引，所以整体含义就是查看当前 ES服务器中的所有索引，就好像 MySQL 中的 show tables 的感觉。



### 查看单个索引

向 ES 服务器发送 GET 请求：

```sh
curl -X GET http://127.0.0.1:9200/shopping | jq
```

服务器返回响应：

```sh
{
  "shopping": {
    "aliases": {},
    "mappings": {},
    "settings": {
      "index": {
        "creation_date": "1647008741621",
        "number_of_shards": "1",
        "number_of_replicas": "1",
        "uuid": "va4GwpL6SXGGIDIXYWuMwQ",
        "version": {
          "created": "7030299"
        },
        "provided_name": "shopping"
      }
    }
  }
}
```



### 删除索引

向 ES 服务器发送 DELETE 请求：

```SH
curl -X DELETE http://127.0.0.1:9200/shopping | jq
```



## 创建文档

假设索引已经创建好了，接下来我们来创建文档，并添加数据。这里的文档可以类比为关系型数据库中的表数据，添加的数据格式为 JSON 格式 。

向 ES 服务器发送 POST 请求：

```sh
curl -X POST -H 'Content-Type: application/json' -d '{     "title":"小米手机",     "category":"小米",     "images":"http://www.gulixueyuan.com/xm.jpg",     "price":3999.00 }' http://127.0.0.1:9200/shopping/_doc | jq
```

由于需要发送 JSON 字符串，用 curl 输入不太直观，所以可以使用 postman：

 <img src="https://img-blog.csdnimg.cn/img_convert/20d54cba223bd9d70ea356d3e40a8161.png" alt="img" style="zoom:80%;" /> 

服务器返回：

```sh
{
    "_index": "shopping",//索引
    "_type": "_doc",//类型-文档
    "_id": "ANQqsHgBaKNfVnMbhZYU",//唯一标识，可以类比为 MySQL 中的主键，随机生成
    "_version": 1,//版本
    "result": "created",//结果，这里的 create 表示创建成功
    "_shards": {//
        "total": 2,//分片 - 总数
        "successful": 1,//分片 - 总数
        "failed": 0//分片 - 总数
    },
    "_seq_no": 0,
    "_primary_term": 1
}
```

上面的数据创建后，由于没有指定数据唯一性标识（ID），默认情况下， ES 服务器会随机生成一个。

如果想要自定义唯一性标识，需要在创建时指定： http://127.0.0.1:9200/shopping/_doc/1

服务器返回：

```sh
{
    "_index": "shopping",
    "_type": "_doc",
    "_id": "1",//<------------------自定义唯一性标识
    "_version": 1,
    "result": "created",
    "_shards": {
        "total": 2,
        "successful": 1,
        "failed": 0
    },
    "_seq_no": 1,
    "_primary_term": 1
}
```



## 查询文档

### 查询所有文档

查看索引下所有文档，向 ES 服务器发 GET 请求 ： http://127.0.0.1:9200/shopping/_search

服务器返回：

```sh
{
    "took": 133,
    "timed_out": false,
    "_shards": {
        "total": 1,
        "successful": 1,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": {
            "value": 2,
            "relation": "eq"
        },
        "max_score": 1,
        "hits": [
            {
                "_index": "shopping",
                "_type": "_doc",
                "_id": "ANQqsHgBaKNfVnMbhZYU",
                "_score": 1,
                "_source": {
                    "title": "小米手机",
                    "category": "小米",
                    "images": "http://www.gulixueyuan.com/xm.jpg",
                    "price": 3999
                }
            },
            {
                "_index": "shopping",
                "_type": "_doc",
                "_id": "1",
                "_score": 1,
                "_source": {
                    "title": "小米手机",
                    "category": "小米",
                    "images": "http://www.gulixueyuan.com/xm.jpg",
                    "price": 3999
                }
            }
        ]
    }
}
```



### 查询单个文档

查看文档时，需要指明文档的唯一性标识，类似于 MySQL 中数据的主键查询

在 Postman 中，向 ES 服务器发 GET 请求 ： http://127.0.0.1:9200/shopping/_doc/1 。

服务器返回：

```sh
{
    "_index": "shopping",
    "_type": "_doc",
    "_id": "1",
    "_version": 1,
    "_seq_no": 1,
    "_primary_term": 1,
    "found": true,
    "_source": {
        "title": "小米手机",
        "category": "小米",
        "images": "http://www.gulixueyuan.com/xm.jpg",
        "price": 3999
    }
}
```











