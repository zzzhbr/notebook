# 变量内容删除替换

定义变量：
```shell
[root@backup scripts]# echo $Valure
I am smart
```


## 获取变量内容字符长度${#Valure}
```shell
[root@backup scripts]# echo ${#Valure}
10
```

## 变量内容切片${Valure:N}
```shell
[root@backup scripts]# echo ${Valure:2}  #切掉前2个字符
am smart
[root@backup scripts]# echo ${Valure:2:2} #将从第3个字符开始取后面2个字符
am


```
 



