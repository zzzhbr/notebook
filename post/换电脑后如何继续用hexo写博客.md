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
your_email@example.com改成你的账户邮箱即可

一般默认一路回车就好

进入ssh密钥生成目录，一般在命令结束后会有提示保存位置，一般是在C:\Users\用户名\.ssh，然后打开id_rsa.pub文件，复制里面所有的内容，
然后进入 github 页面，点击右上角的 头像 > Settings ，在左侧找到SSH and GPG keys。

点击New SSH key ，Title 里的内容可以自定义，Key 里填入复制的内容。点击 add key。

返回窗口，输入：
```
ssh -T git@github.com
若弹出Are you sure you want to continue connecting (yes/no)? 时输入 yes 确认。
接着出现 Hi xxx! You've successfully authenticated, but GitHub does not provide shell access. 则操作成功。
```

然后可以用命令测试是否成功
```
hexo clean // 清除缓存 网页正常情况下可以忽略此条命令
hexo g // 生成静态网页
hexo s // 启动服务器
hexo d //推送到git上
```

报错
```
Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'zzz@zzz-PC.(none)')
Warning: Permanently added the RSA host key for IP address '13.250.177.223' to the list of known hosts.
Everything up-to-date
Branch 'master' set up to track remote branch 'master' from 'git@github.com:zzzhbr/zzzhbr.github.io.git'.

*** Please tell me who you are.
```
也比较简单，只需要将
```
 git config --global user.email "you@example.com"
 git config --global user.name "Your Name"
```
两条命令的双引号里的内容改成你自己的就可以