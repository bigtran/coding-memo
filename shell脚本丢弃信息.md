shell中使用>/dev/null 2>&1 丢弃信息
 
在一些Shell脚本中，特别是Crontab的脚本中，经常会看到 >/dev/null 2>&1这样的写法。

其实这个很好理解。我们分两部分解释。

1.  >/dev/null

大家知 “>”（右尖括号） 在unix/linux shell 中表示 输入到 的意思，就是把”>”左边的内容输入到”>”右边。

比如：echo text>1.txt 就把“text”这个文本输入到1.txt这个文件中。

那么 “/dev/null” 又是个什么东东呢？它代表一个空设备，即不存在的设备。也就是说，抛弃”>”左边的内容，不进行输出。

2.    2>&1

这个其实是三个部分组成的：2， >&， 1 。我们先来搞清楚这里的2和1是什么意思。在/usr/include/unistd.h中，你可以找到如下代码。

#define STDIN_FILENO    0   #define STDOUT_FILENO   1   #define STDERR_FILENO   2  

这是三种不同的流。

2代表stderr.

1代表sdtout.

而 &> 则表示把符号左边的内容以符号右边的形式输出。

2&>1 就是把，把stderr做为stdout输出。

现在我们结合这两个部分来看。2&>1定义了把stderr做为标准的stdout流输出，然后stdout的内容全部写入/dev/null，也就是说被舍弃掉。

结论就是，无论执行的是什么命令，哪怕运行中出现了error都不会有回显。