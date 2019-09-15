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
|column1|column2|
|-|-|
|${Valure:N} |删除到第几个字符|
|${Valure:N:N} | 第二个N代表步长|

|column1|column2|
|-|-|
|${Valure#匹配规则}|从变量开头进行匹配,把匹配到的第一个的前面的内容全部删除|
|${Valure##匹配规则}|从变量开头进行匹配,把匹配到底最后一个
的 前面的内容全部删除|
|||
|||

  


${Valure%匹配规则}
${Valure%%匹配规则}

${Valure/旧字符串/新字符串}
${Valure//旧字符串/新字符串}




## 变量内容切片
```shell
[root@backup scripts]# echo ${Valure:2}  #切掉前2个字符
am smart
[root@backup scripts]# echo ${Valure:2:2} #将从第3个字符开始取后面2个字符
am
```
 
## 变量内容删除




url=www.25share.com
echo $url


