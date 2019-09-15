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

符合旧字符串的 .  第一个匹配到的会被新字符串 , 取代
[root@backup scripts]# echo ${url/./,}
www,25share.com

符合旧字符串的 .  全部匹配到的会被新字符串 , 取代
[root@backup scripts]# echo ${url//./,}
www,25share,com




例子二：
URL=www.25.com.share.com.25
符合旧字符串的 com 第一个匹配到的会被新字符串 cn 取代
[root@backup scripts]# echo ${URL/com/cn}
www.25.cn.share.com.25
符合旧字符串的 com 全部匹配到的会被新字符串 cn 取代
[root@backup scripts]# echo ${URL//com/cn}
www.25.cn.share.cn.25
```


# 变量计算
## 变量自增
a++ 与 ++a的区别
- a++ 先引用后增加；先赋值后运算
 > 先让a所在的表达式中使用当前的值，然后让a+1
- ++a 先增加后引用；；先运算后赋值
 > a先自加

`let` 运算

```shell
一、
[root@backup ~]# a=1
[root@backup ~]# b=1
[root@backup ~]# let x=a+1
[root@backup ~]# let y=++b
[root@backup ~]# echo $x
2
[root@backup ~]# echo $y
2
[root@backup ~]# echo $a
1
[root@backup ~]# echo $b
2



二、
[root@backup ~]# a=1
[root@backup ~]# b=1
[root@backup ~]# let x=++a
[root@backup ~]# 
[root@backup ~]# let y=b++
[root@backup ~]# echo $x
2
[root@backup ~]# echo $y
1
[root@backup ~]# echo $a
2
[root@backup ~]# echo $b
2
```

## 变量

