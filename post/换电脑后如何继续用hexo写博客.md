如何在更换电脑后如何继续用hexo写博客
<!--more-->

# 1.安装必要的软件
- git
- node.js
软件按照正常安装即可


# 2. blog源目录拷贝
一种是将旧电脑中的blog目录拷贝；
另一种就是github上直接下载

# 3. hexo
安装hexo
在CMD中输入安装指令，可以使用`-g`全局安装
```
npm install hexo-cli -g
```

# 4. 生成新的ssh-key
```
ssh-keygen -t rsa -C "your_email@example.com"
```

一般默认一路回车就好
