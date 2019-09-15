# shell脚本位置参数

> 位置参数：脚本传参

## $0
> 脚本名称
如果是全路径执行，那么获取的是全路径名称

```shell
basename：无论是否全路径，获取的都是名字
[ ]# basename test.sh
test.sh
[ ]# basename /server/scripts/test.sh
test.sh

```
```shell
dirname：无论是否全路径，获取的都是路径名
[root@backup scripts]# dirname 1.sh
.
[root@backup scripts]# dirname /server/scripts/1.sh
/server/scripts
```

## $n
> 脚本的第n个参数 

$1: 第一个参数
$2: 第二个参数
$3: 第三个参数
...
${10}  $10 相当于$1 后面跟个
${11}
${12}


## $#
> 脚本传参的总个数

```shell
[root@backup scripts]# cat canshu.sh 
#!/bin/bash
echo this is $0
echo "$1 $2"
echo $#

[root@backup scripts]# sh canshu.sh 1 2
this is canshu.sh
1 2
2
```




## $* 
> 获取传参的所有参数，如果不加双引号和$@相同
> 如果加上双引号，获取的是一个整体

## $@
> 获取传参的所有参数，如果不加双引号和$*相同
> 如果加上双引号，获取的为单个参数


```diff shell
[root@backup scripts]# set -- "I have" a  dog
#用 set 模拟传参

#不加双引号，效果一致
[root@backup scripts]# for i in $*;do echo $i;done
I
have
a
dog
[root@backup scripts]# for i in $@;do echo $i;done
I
have
a
dog

#加了双引号的不同
[root@backup scripts]# for i in "$*";do echo $i;done
- I have a dog
[root@backup scripts]# for i in "$@";do echo $i;done
- I have
- a
- dog

```
## $?
> 上一条命令的执行结果，<font color=red>**0**</font> 为成功，<font color=red>**非0**</font> 为不成功

## $$
> 获取当前shell的进程PID
当系统执行多个shell脚本时使用

## $!
> 获取上一个脚本的PID
拍错时可能会用到

## $_

<font color=red>red</font>