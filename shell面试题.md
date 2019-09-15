# 案例一：取出小于3的字符串
示例字符： `I am smart`

解法一：
```shell
[root@backup scripts]# echo "I am smart"|xargs -n1|awk '{if(length<3) print}'
I
am

```
