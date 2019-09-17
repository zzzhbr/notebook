# 案例一：取出小于3的字符串
示例字符： `I am smart`

解法一：
```shell
[root@backup scripts]# echo "I am smart"|xargs -n1|awk '{if(length<3) print}'
I
am

```

解法二：
```shell
[root@backup scripts]# echo "I am smart"|awk '{for(i=1;i<NF;i++)if(length($i)<3) print $i}'
I
am

#这里的空格可有可无，都能正确执行
[root@backup scripts]# echo "I am smart"|awk '{for(i=1;i<NF;i++) if(length($i)<3) print $i}'
I
am

[root@backup scripts]# echo "I am smart"|awk '{for (i=1;i<NF;i++) if (length($i)<3) print $i}'
I
am

```

解法三：
```shell
[root@backup scripts]# vim 2.sh
#!/bin/bash 
for i in I am smart 
do 
  if [ $(#i) -lt 3 ] 
  then 
    echo $i 
  fi 
done 

# $(#i)  取 字符串 长度
```
