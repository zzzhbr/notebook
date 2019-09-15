# 变量内容查看

临时定义变量：
```shell
[root@backup scripts]# Valure="I am smart"
```

## 查看变量内容
```shell
[root@backup scripts]# echo $Valure
I am smart
```


## 获取变量内容字符长度

1. ${#Valure}
```shell
[root@backup scripts]# echo ${#Valure}
10
```
2. wc
由结果中看 `wc -L` 最为准确
> -L 显示最长行的长度;但是变量赋值一般是只有一行
```shell
[root@backup scripts]# echo ${Valure} |wc -c
11
[root@backup scripts]# echo ${Valure} |wc -L
10
[root@backup scripts]# echo ${Valure} |wc -l
1
[root@backup scripts]# echo ${Valure} |wc -m
11
```

3. awk '{print length}'
```shell
[root@backup scripts]# echo $Valure | awk '{print length}'
10
```

4. expr length
```shell
[root@backup scripts]# expr length "$Valure"
10
```

# 变量内容删除替换

示例：
`url=www.25share.com`
`echo $url`


1. 类似切片

|语法|作用|
|-|-|
|${Valure:N} |删除到第几个字符|
|${Valure:N:N} | 第二个N代表步长|

```shell
1. 
[root@backup scripts]# echo ${url:4}
25share.com

2. 
[root@backup scripts]# Valure="I am smart"
[root@backup scripts]# echo ${Valure:2}  #切掉前2个字符
am smart
[root@backup scripts]# echo ${Valure:2:2} #将从第3个字符开始取后面2个字符
am
```





2. 开头开始匹配

|语法|作用|
|-|-|
|${Valure#匹配规则}|从变量**开头**进行匹配,把匹配到的 **第一个的** 前面的内容全部删除|
|${Valure##匹配规则}|从变量**开头**进行匹配,把匹配到的 **最后一个的** 前面的内容全部删除|

```shell
从头开始将匹配到的第一个.前面的任意内容删除  ==>  www.删除
[root@backup scripts]# echo ${url#*.}
25share.com

从头开始将匹配到的最后一个.匹配到的任意内容  ==>  www.25share.删除
[root@backup scripts]# echo ${url##*.}
com
```



3. 结尾开始匹配

|语法|作用|
|-|-|
|${Valure%匹配规则}|从变量**尾部**进行匹配,把匹配到的 **第一个的** 后面的内容全部删除|
|${Valure%%匹配规则}|从变量**尾部**进行匹配,把匹配到的 **最后一个的** 后面的内容全部删除|



```shell
从尾部开始将匹配到的第一个.后面的任意内容删除  ==>  .com删除
[root@backup scripts]# echo ${url%.*}
www.25share


从尾部开始将匹配到的最后一个.后面的任意内容删除  ==>  .25share.com删除
[root@backup scripts]# echo ${url%%.*}
www
```






4. 字符替换

|语法|作用|
|-|-|
|${Valure/旧字符串/新字符串}|符合旧字符串的变量内容，**第一个** 会被新字符串取代|
|${Valure//旧字符串/新字符串}|符合旧字符串的变量内容，**全部的** 会被新字符串取代|

```shell
将www.删除
[root@backup scripts]# echo ${url/www./}
25share.com

例子：
URL=www.25.comshare.com

```







