# Linux 单节点部署

## 下载

官网下载地址：[https://www.elastic.co/cn/downloads/elasticsearch](https://www.elastic.co/cn/downloads/elasticsearch)

选择合适的版本下载，可以在 windows 下载后 上传到 linux。

> 注意由于 es 和 jdk 是一个强依赖的关系，所以当我们在新版本的 es 压缩包中包含有自带的 jdk，但是当我们的 linux 中已经安装了 jdk 之后，就会发现启动 es 的时候优先去找的是 linux 中已经装好的 jdk，此时如果 jdk 的版本不一致，就会造成 jdk 不能正常运行 。具体 es 和 jdk 的对应版本参考：[https://www.elastic.co/cn/support/matrix#matrix_browsers](https://www.elastic.co/cn/support/matrix#matrix_browsers)

也可以在Linux命令行，直接执行以下命令进行下载（下载比较慢）：

```sh
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.3.2-linux-x86_64.tar.gz
```



## 解压

```sh
# ES的下载位置
cd /home/changyansong/Elasticsearch/
tar -zxvf elasticsearch-7.3.2-linux-x86_64.tar.gz
```



## 创建用户

因为安全问题， ES 不允许 root 用户直接运行，所以要创建新用户。

由于我用的是自己的用户，所以这一步可以跳过。



## 修改配置文件

修改配置文件：`/home/changyansong/Elasticsearch/elasticsearch-7.3.2/config/elasticsearch.yml`

```sh
# 加入以下配置
cluster.name: elasticsearch
node.name: node-1
network.host: 0.0.0.0
http.port: 9200
cluster.initial_master_nodes: ["node-1"]
```



## 启动

```sh
cd /home/changyansong/Elasticsearch/elasticsearch-7.3.2/bin/
# 前台启动
./elasticsearch
# 后台启动
./elasticsearch -d
```

启动后可以使用 `jps` 命令看到后台 ES 进程。



## 测试

测试是否成功启动，输入命令：`curl http://localhost:9200`。

服务器返回：

```sh
{
  "name" : "icx31",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "y0X2KKjdQnWPG1kWgJH9qQ",
  "version" : {
    "number" : "7.3.2",
    "build_flavor" : "default",
    "build_type" : "tar",
    "build_hash" : "1c1faf1",
    "build_date" : "2019-09-06T14:40:30.409026Z",
    "build_snapshot" : false,
    "lucene_version" : "8.1.0",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}

```







































