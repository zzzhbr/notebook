# 变量内容删除替换

定义变量：
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
-L 显示最长行的长度;但是变量赋值一般是只有一行
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

## 变量内容切片${Valure:N}
```shell
[root@backup scripts]# echo ${Valure:2}  #切掉前2个字符
am smart
[root@backup scripts]# echo ${Valure:2:2} #将从第3个字符开始取后面2个字符
am
```
 



