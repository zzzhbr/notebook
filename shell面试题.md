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
