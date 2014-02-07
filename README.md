CommLib
=======

linux常用库,使用boost和标准库编写的常用库,包含线程池、内存池、通信、日志、时间处理、定时器
2014/1/29
目前问题:
1、内存池效率较低，测试结果是默认分配的20分之一左右，因为分配和回收队列都采用的std::deque，该结构也是动态分配的内存，导致效率问题
2、网络库比较简单，异常情况考虑较少，功能也比较简单，考虑在之上实现一个简单易用的网络库+通信协议
3、日志库还未实现

2014/2/7
更详细测试:
1、采用自己编写的list,内存池效率有所提高,大概为默认分配的1/9左右:
99线程,100000任务,每个任务从1到1000字节分配内存:

默认内存分配:
m:8 hm-205794

加锁机制调整后:
m:70 hm112758

耗时操作主要有hash耗时和分配耗时,其中hash耗时9s左右

2、99线程,100000任务,每个任务从1到10000字节分配内存:
*10:
bithash
m:408 hm-845658
默认hash
m:673 hm190934

默认分配:
m:18 hm52901
m:19 hm-278459


