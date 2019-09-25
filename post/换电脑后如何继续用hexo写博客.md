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
然后进入blog目录,按住shift点击在此处打开命令行终端
```
npm install
```

# 4. 生成新的ssh-key
```
ssh-keygen -t rsa -C "your_email@example.com"
```

一般默认一路回车就好

进入ssh密钥生成目录，一般C:\Users\用户名.ssh，打开id_rsa.pub文件，复制里面所有的内容，然后进入 github 页面，点击右上角的 头像 > Settings ，在左侧找到SSH and GPG keys。

点击New SSH key ，Title 里的内容可以自定义，Key 里填入复制的内容。点击 add key。

返回窗口，输入：

Copy
ssh -T git@github.com
若弹出Are you sure you want to continue connecting (yes/no)? 时输入 yes 确认。

接着出现 Hi xxx! You've successfully authenticated, but GitHub does not provide shell access. 则操作成功。
