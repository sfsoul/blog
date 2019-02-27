### 官网下载地址
https://redis.io/download

### 安装步骤
```
1. cd /usr/local
2. wget http://download.redis.io/releases/redis-5.0.3.tar.gz
3. tar xzf redis-5.0.3.tar.gz
4. cd redis-5.0.3
5. make
6. make test // 编译测试
7. make install  // 编译安装
```
依次完成上述步骤后，即可代表已成功安装 redis到mac上了。
接下来就是启动redis。

### 启动redis（服务端）
启动redis的命令很简单：
```
// 1.先跳转到redis的安装目录
cd /usr/local/redis-5.0.3

// 2. 执行redis-server命令
redis-server
```
![redis-server](https://note.youdao.com/yws/public/resource/7c8e76bd597413ed1f18d54bb6f862e3/xmlnote/E9D6483CAC6342F988708B64BB9EC135/45338)

**当看到这上面这幅图时，即说明redis已经成功启动啦。进程ID为：55182，端口为：6379。**

### 启动redis（客户端）
```
// 只需要到redis的安装目录下执行redis-cli命令即可。
cd /usr/local/redis-5.0.3

redis-cli
```
**此时会按照默认配置连接Redis（127.0.0.1:6379）**
### 查看redis进程
```
ps -ef | grep -i redis
```
![查看redis进程](https://note.youdao.com/yws/public/resource/7c8e76bd597413ed1f18d54bb6f862e3/xmlnote/20475E0F54B1471EBBD0BB8C36D4FE17/45340)

### 关闭服务端
**关闭服务端有两种方法：**
#### 强行关闭
**强行终止redis进程可能会导致数据丢失，因为redis可能正在将内存数据同步到硬盘中。**
```
// 查找redis-server的PID
ps -ef | grep -i redis

// kill掉该进程
kill -9 PID
```
#### 命令关闭（推荐使用）
**向redis发送`SHUTDOWM`命令。redis收到命令后，服务端会断开所有客户端的连接，然后根据配置执行持久化，最后退出。**
```
// 启动客户端
redis-cli

// 输入退出命令
SHUTDOWN
```
![SHUTDOWN](https://note.youdao.com/yws/public/resource/7c8e76bd597413ed1f18d54bb6f862e3/xmlnote/41CCC3259FE0444EB456F815169EBB9B/45342)

![close redis](https://note.youdao.com/yws/public/resource/7c8e76bd597413ed1f18d54bb6f862e3/xmlnote/24880563C9AD4CDAA794703819F4BF39/45344)
### 安装过程中遇到的问题
#### 提示 wget 命令不存在
**提示这个是因为`wget`不存在，判断存不存在可以通过输入`cd /usr/local/bin`，然后输入命令`ls`即可知道。**

**建议用homebrew去安装wget：**
```
brew install wget
```
安装完`wget`之后，也可以通过`cd /usr/local/bin`去检查下是否已经存在`wget`了。
若已经存在，则可继续执行后面的命令。

#### tar xzf redis-5.0.3.tar.gz执行时出错
我在执行`tar xzf redis-5.0.3.tar.gz`的时候，终端打印出了一堆错误，开始是有点懵逼的。
然后在命令前加上`sudo`就完美解决了这个问题。
```
sudo tar xzf redis-5.0.3.tar.gz
```

### 参考文章
- [Redis: Failed opening .rdb for saving: Permission denied](https://stackoverflow.com/questions/22160753/redis-failed-opening-rdb-for-saving-permission-denied/28686802)
- [mac下安装redis](https://zhuanlan.zhihu.com/p/35945728)