# 安装 rally

## 安装 python

由于 rally 要求 python 3.8 以上，所以需要重新下载一个 python 版本。

注：pyenv 是一个 python 版本管理工具，可以在同一个系统中切换不同的 python 版本。但由于安装过程中出现问题，且未能解决，**所以选择自己手动下载 python 安装包，并且手动执行 python 和 pip 命令**。

1. 进入 python 下载官网，选择合适的压缩包：https://www.python.org/ftp/python/
2. 解压后，进入到解压后的主目录下，执行以下命令，进行编译，生成 python3 目录。

```sh
cd /home/changyansong/Python/Python-3.8.10/

./configure --prefix=/home/changyansong/Python/Python-3.8.10/

make && make install
```

3. 进入到编译后的目录下，测试是否安装成功：

```sh
cd /home/changyansong/Python/Python-3.8.10/python3/bin/

# 查看 python 版本
./python3 --version
```



## 安装 pip

1. 获取 pip 的安装文件（如果网址无法访问，可以手动访问后复制出来，然后自己新建 py 文件粘贴进去）

```sh
wget https://bootstrap.pypa.io/get-pip.py
```

2. 安装 pip：

```sh
cd /home/changyansong/Python/Python-3.8.10/python3/bin/

./python3 get-pip.py
```

3. 执行成功后，就会在当前 bin 目录下生成 pip3，测试是否安装成功：

```sh
./pip3 --version
```



## 安装 esrally

```sh
cd /home/changyansong/Python/Python-3.8.10/python3/bin/

./pip3 install esrally
```

安装好后可以测试一下是否安装成功：

```sh
esrally --version
```



## 数据准备

track 是赛道的意思，在这里是指压测用的数据和测试策略，track.json 便是压测策略的定义文件。

压测的工作，无非就是以下几个步骤：

- 指定/创建目标 ES 集群

- 创建索引、mapping
- 导入样本数据
- 进行读写操作
- 汇报压测结果

由于 Rally 运行时，需要从外网下载数据，所以改为手动下载。 



### 下载压测场景的配置（track）

```sh
# rally 下载后会在用户根目录生成 .rally 文件夹
mkdir -p ~/.rally/benchmarks

cd ~/.rally/benchmarks

git clone https://github.com/elastic/rally-tracks.git
```

查看 rally-tracks 项目提供的现成压测场景： 

```sh
esrally list tracks
```

跑 list 命令时，rally 自动做了一个 copy 动作 :

```sh
cd ~/.rally/benchmarks

mkdir tracks
# 将 rally-tracks 复制到一个新的目录 tracks/default 中
cp -r rally-tracks tracks/default
```

所以 rally-tracks 目录可以删掉了 ：

```sh
rm -rf rally-tracks
```



### 下载样本数据（data）

从 list 命令可以知道，不同的压测场景，样本数据的体积不一样。可以根据需求，下载需要的数据。这里以 geopoint 为例。 

```sh
cd /home/changyansong/.rally/benchmarks/tracks/default/
# download.sh 是 esrally 提供的自动下载数据集的脚本
./download.sh geopoint
# 下载后会在当前目录下生成 rally-track-data-geopoint.tar，解压到用户根目录
# 解压后，会自动在 ~/.rally/benchmarks/ 下新建 data/geopoint 目录，样本数据就保存在其中
tar -xvf rally-track-data-geonames.tar -C ~/
```



## 测试 esrally

启动 ES 后，在 geopoint 场景下测试 esrally：

```bash
esrally race --pipeline=benchmark-only --target-hosts=127.0.0.1:9200 --offline --track=geopoint  --challenge=append-no-conflicts
```

























