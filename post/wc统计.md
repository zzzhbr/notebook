```
[root@backup scripts]# wc --help
用法：wc [选项]... [文件]...
　或：wc [选项]... --files0-from=F
Print newline, word, and byte counts for each FILE, and a total line if
more than one FILE is specified.  With no FILE, or when FILE is -,
read standard input.  A word is a non-zero-length sequence of characters
delimited by white space.
The options below may be used to select which counts are printed, always in
the following order: newline, word, character, byte, maximum line length.
  -c, --bytes            print the byte counts   
  -m, --chars            print the character counts
  -l, --lines            print the newline counts
      --files0-from=文件	从指定文件读取以NUL 终止的名称，如果该文件被
					指定为"-"则从标准输入读文件名
  -L, --max-line-length	显示最长行的长度
  -w, --words			显示单词计数
      --help		显示此帮助信息并退出
      --version		显示版本信息并退出

GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
请向<http://translationproject.org/team/zh_CN.html> 报告wc 的翻译错误
要获取完整文档，请运行：info coreutils 'wc invocation'

```





![title](https://raw.githubusercontent.com/zzzhbr/notebook-image/master/notebook/2019/09/15/1568532456955-1568532456983.png)