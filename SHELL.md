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
${10}  $10 相当于$1 后面跟个0
${11}
${12}


## $#
> 脚本传参的总个数

## $@