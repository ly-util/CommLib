CommLib
=======

linux常用库,使用boost和标准库编写的常用库,包含线程池、内存池、通信、日志、时间处理、定时器
2014/1/29
目前问题:
1、内存池效率较低，测试结果是默认分配的20分之一左右，因为分配和回收队列都采用的std::deque，该结构也是动态分配的内存，导致效率问题
2、网络库比较简单，异常情况考虑较少，功能也比较简单，考虑在之上实现一个简单易用的网络库+通信协议
3、日志库还未实现
