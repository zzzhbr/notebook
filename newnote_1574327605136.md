# 1. 安装
首先安装添加mac选项的工具

然后修改创建的mac的修改VMX
在smc.present = "TRUE"下面添加下面内容即可 （右键以记事本方式打开即可）
```
smc.version = "0"
```
然后就可以开始安装MacOS了
安装过程只需要耐心些就好，速度快慢全看配置，内存太低的<8G的就不要尝试了，就算装好了，我估计也是卡死

# 2. 全屏
安装完成以后不能全屏，
所以先安装vmtools，安装完vmtools若是还是没有分辨率更改的话，那么就要进行以下操作了


首先将com.vmware.fusion.tools.windows.zip.tar包放进mac系统里
然后在Mac虚拟机里的终端执行下面的命令，执行完之后关机
```mac
sudo nvram AC20C489-DD86-4E99-992C-B7C742C1DDA9:width=%80%07%00%00
sudo nvram AC20C489-DD86-4E99-992C-B7C742C1DDA9:height=%38%04%00%00
```


接着修改mac的vmx加入以下代码（右键以记事本方式打开即可）
```
svga.autodetect = "FALSE"
svga.maxWidth = "3840"
svga.maxHeight = "2160"
```

最后开启
就能看到高分辨率了，就能全屏了


# 3. 文件共享
最后如果你想要实现mac和win文件共享，那么可以进行以下操作
虚拟机关机
然后
 <div align=center>
	<img src="https://raw.githubusercontent.com/zzzhbr/notebook-image/master/gitnote/2019/11/21/1-1574328181217.png" alt="设置" width = "40%" height = "40%">
</div>




此方法如不成功，可以用以下方式操作
选择用来共享的文件夹
右键 -----> 属性 -----> 共享
以这种方式来共享


win设置好了以后就可以去mac系统操作访问测试了

<div align=center>
	<img src="https://raw.githubusercontent.com/zzzhbr/notebook-image/master/gitnote/2019/11/21/2-1574328342280.png" alt="测试" width = "40%" height = "40%">
</div>


输入smb://win系统IP地址
连接测试

如果连接不上去，可以去看看win系统的设置`win+r`，输入`secpol.msc`
然后看看这里的权限等开启了没有

<div align=center>
	<img src="https://raw.githubusercontent.com/zzzhbr/notebook-image/master/gitnote/2019/11/21/3.-1574328494286.png" alt="测试" width = "40%" height = "40%">
</div>


总的来说就是
1，在运行里面输入"secpol.msc"来启动本地安全设置，然后选择本地策略-->安全选项 -->网络安全LAN 管理器身份验证级别，“安全设置”选项默认是“没定义”。修改成“发送 LM 和 NTMLM响应(&)”或者“发送 LM 和 NTMLM - 如果已协商，则使用NTLMv2 会话安全”

2，如果不行，看刚才打开的本地安全设置里，本地策略-->安全选项 -->来宾账户状态这个选项是禁用的，打开查看。大致意思是说明这个选项关闭的话SMB服务就无法使用，因为UNIX用于共享的就是SMB服务，于是将其打开。

3，如果还是不行，还是在安全选项里，将网络访问：本地账户的共享和安全模型设置为“经典”。

然后回到mac重新连接就成功了
