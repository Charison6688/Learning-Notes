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





