# 目标

在跳板机（IP：crt-e302.sh.intel.com）的 VNC 图形化界面上使用 IDEA，但该 IDEA 部署在远程服务器上。

# 步骤

1. 在 mobaxsterm 上使用普通用户登录跳板机，运行命令：`vncserver -geometry 1920x1080`，其中，1920x1080 是分辨率，记住输出的端口号，如8；	
2. windows 笔记本安装 vnc-client ，创建连接，<跳板机ip>:端口号，端口号是第一步的结果；输入密码。

1. 在 vnc 中连接跳板机，然后在终端中运行命令：`xhost +`，关闭权限控制：
2. 在 vnc 终端中进入远程服务器，在终端中运行以下命令，这样在远程服务器上运行的GUI程序都会输出到跳板机的 vnc 的图形化界面上。

```bash
ssh icx31

# export DISPLAY=<跳板机IP>:端口号
export DISPLAY=crt-e302.sh.intel.com:8
```

1. 在远程服务器的终端中运行 IDEA 的图形化启动脚本，即可在跳板机上使用远程服务器上的 IDEA。

```bash
cd IDEA/idea-IC-213.6777.52/bin/

./idea.sh
```

<img src="Linux 搭建 Elasticsearch.assets/1646980507853.png" alt="1646980507853" style="zoom: 60%;" />