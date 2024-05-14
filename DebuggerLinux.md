# Using the GUN Debugger linux

## about gcc
gcc test.c 会生成一个a.out的可执行文件文件；但是没有用于debug的信息
然后用./可执行文件就能执行该文件的程序了

但a.out过多容易引起混乱；
所以用下面这个命令
gcc test.c -o test.out
编译的时候将可执行文件名重命名一下，可以很容易就区分还out文件是那个c文件的;

因为我们希望可执行文件尽可能的快和小，所以没有放进去debug symbol;
gcc -g test.c -o test.out 
-g命令可以将debug symbol添加到我们的可执行文件当中

怎么开始调试呢？
gdb ./test.out

b main  ：给main打断点

b 路径：行数  b /home/kkbond/Code/test.c:10

r ：执行

n: 单步执行，不进入函数

s: 单步执行，进入函数；

k:kill the program debugged;从调试中退出

info b;可以查看所有的断点；

d num:删除断点，与info b 配合使用，info b会给出所有断点的num;

c: cong这一个断点直接到下一个断点，不进行step调试；

bt:查看函数调用栈；

watch point:监视某个点或变量，一旦被监视者发生了变化，那么就停止程序,停在变化的量的下面一行；

回车： 执行上一个命令；

