### IO模型

同步/异步  阻塞/非阻塞

IO多路复用模型 
多个链接公用一个等待机制，可以实现多路复用，也会阻塞请求，只是阻塞位置不同

信号驱动IO模型

磁盘考入内存不需要阻塞，数据拷贝进入缓冲期间阻塞。

异步IO模型

完全异步，拷贝完成后再通知进程。


直接内存映射。

Nginx使用epoll



select/poll/epoll

Nginx 可以当做代理服务器使用，代理请求到后端。Nginx 充当客户端的功能。



### 特性

模块化好 不停机更新 低内存消耗 event-driven aio mmap sendfile

### 基本功能

1. 静态资源web服务器 
2. http反向代理服务器  
3. FastCGL(LNMP) uWSGI(python)等协议 等

### nginx 程序架构

1. 虚拟主机（server） 
2. 支持keep-alive和管道连接 
3. 访问日志 
4. url rewirte 地址重写
5. 路径别名
6. 基于IP及用户的访问控制

### ngix 架构

模块分类： 
1. 核心模块：core module 
2. 标准模块： http、mail、stream
3. 第三方模块

### nginx 功能

1. 静态web资源服务器
2. 请求转发(只转发请求)反向代理（对请求进行解析然后自己访问）




