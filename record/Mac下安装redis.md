### 官网下载地址
https://redis.io/download

### 安装步骤
```
1. cd /usr/local
2. wget http://download.redis.io/releases/redis-5.0.3.tar.gz
3. tar xzf redis-5.0.3.tar.gz
4. cd redis-5.0.3
```

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
