# 下载和解压安装包

- 官网下载地址：[https://www.elastic.co/cn/downloads/elasticsearch](https://www.elastic.co/cn/downloads/elasticsearch)

  选择合适的版本下载，可以在 win 下载后 上传到 linux。

  > 注意由于 es 和 jdk 是一个强依赖的关系，所以当我们在新版本的 es 压缩包中包含有自带的 jdk，但是当我们的 linux 中已经安装了 jdk 之后，就会发现启动 es 的时候优先去找的是 linux 中已经装好的 jdk，此时如果 jdk 的版本不一致，就会造成 jdk 不能正常运行 。具体 es 和 jdk 的对应版本参考：[https://www.elastic.co/cn/support/matrix#matrix_browsers](https://www.elastic.co/cn/support/matrix#matrix_browsers)

   也可以在Linux命令行，直接执行以下命令进行下载（下载比较慢）：

  ```sh
  wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.3.2-linux-x86_64.tar.gz
  ```

-  执行解压缩命令：

  ```sh
  tar -zxvf elasticsearch-7.3.2-linux-x86_64.tar.gz
  ```

  



































