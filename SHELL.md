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
basename：无论是否全路径，获取的都是名字
[ ]# basename test.sh
test.sh
[ ]# basename /server/scripts/test.sh
test.sh

```

## $n
> 脚本的第n个参数 