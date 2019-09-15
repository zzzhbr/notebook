```shell
[root@backup scripts]# wc --help
用法：wc [选项]... [文件]...
　或：wc [选项]... --files0-from=F
Print newline, word, and byte counts for each FILE, and a total line if
more than one FILE is specified.  With no FILE, or when FILE is -,
read standard input.  A word is a non-zero-length sequence of characters
delimited by white space.
The options below may be used to select which counts are printed, always in
the following order: newline, word, character, byte, maximum line length.
  -c, --bytes            print the byte counts   打印字节数
  -m, --chars            print the character counts 打印字符数
  -l, --lines            print the newline counts   打印行数
      --files0-from=文件	从指定文件读取以NUL 终止的名称，如果该文件被
					指定为"-"则从标准输入读文件名
  -L, --max-line-length	显示最长行的长度
  -w, --words			显示单词计数
      --help		显示此帮助信息并退出
      --version		显示版本信息并退出
```

测试文档:
```shell
[root@backup scripts]# cat>1.txt<<EOF
> I am smart
> I have a dog
> we are friends
> ohhhhh enjoy it!!!!
> EOF
[root@backup scripts]# cat 1.txt 
I am smart      10
I have a dog    12
we are friends  14
ohhhhh enjoy it!!!! 19
总字数应该为55
```
```shell
[root@backup scripts]# wc -c 1.txt   #统计字节数
59 1.txt
[root@backup scripts]# wc -m 1.txt  #统计字符数
59 1.txt
[root@backup scripts]# wc -l 1.txt  #统计行数
4 1.txt
[root@backup scripts]# wc -L 1.txt  #统计最长行数的字数长度
19 1.txt
[root@backup scripts]# wc -w 1.txt  #统计单词数
13 1.txt
```

但是实际字数统计的话应该为55，但是可以看到无论`-c` 还是 `-m`显示的都是59，这是为什么？
其实是因为制表符的
![title](https://raw.githubusercontent.com/zzzhbr/notebook-image/master/notebook/2019/09/15/1568532456955-1568532456983.png)
