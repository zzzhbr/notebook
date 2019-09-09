
windows右键菜单添加新的程序

<!--more-->

比如我想将XShell添加到右键菜单上面，能够更快速的打开

这里是利用修改注册表的方式：

按下`win+r`输入`regedit`
然后找到
`HKEY_CLASSES_ROOT`下面的`Directory`下面的`Background`里的`shell`;
在`shell`下右键添加`项`，这里比如我添加的是`xshell`，然后在新建的这个xshell下再新建项，比如我命名的是`command`，然后点击`command`，在右边的窗口双击，在`数据数值`里添加程序的绝对路径
![添加过程](https://raw.githubusercontent.com/zzzhbr/notebook-image/master/notebook/2019/09/09/1568030122576-1568030122598.png)

然后就能