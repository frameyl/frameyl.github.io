POSIX代表 “可移植操作系统接口” Portable Operation System Interface 。目的是为了统一不同操作系统之间的系统调用。值得注意的是，POSIX接口不一定是由C来调用，只是最初是由C语言实现的。
C语言的POSIX库是C标准库的超集，定义很多操作系统层面支持的功能，比如socket接口以及thread接口。
下面介绍一下重要的POSIX调用，

######<aio.h> - 异步IO相关的函数
关于异步IO可以说的很多，其目的就是为了提高程序的性能。貌似现在Linux对aio的支持有Bug，而windows支持的更好一点。真是奇葩的很。

######<arpa/inet.h> - IP地址相关的函数

######<dirent.h> - 顾名思义directory entry
这个头文件包含了对目录操作的一些调用

######<fcntl.h> - 文件操作
包括了最常用的open()，close()等函数

######<iconv.h> - 对于多语言的支持
######<malloc.h> - 堆内存的一些高级操作和统计
######<netdb.h> - 主机名服务名协议名等等操作
######<netinet/in.h> - IP地址结构的定义，已经网络主机字节序转换
######<sys/socket.h> - socket相关的一些定义
######<sys/stat.h> - 文件属性相关的定义
######<sys/un.h> - Unix socket相关的操作
######<time.h> - 时间相关的结构和操作
######<unistd.h> - 提供系统调用接口，基本都是要进入的内核态的操作。
######<wchar.h> - 标准C99已经把这个放在C标准库里。
