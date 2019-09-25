打开记事本软件，新建一个文本，复制上以上内容：
```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\.txt]

@="txtfile"

"Content Type"="text/plain"

[HKEY_CLASSES_ROOT\.txt\ShellNew]

"NullFile"="" [HKEY_CLASSES_ROOT\txtfile]

@="文本文档"

[HKEY_CLASSES_ROOT\txtfile\shell]

[HKEY_CLASSES_ROOT\txtfile\shell\open]

[HKEY_CLASSES_ROOT\txtfile\shell\open\command]

@="NOTEPAD.EXE %1"
```

然后存为 `txt.reg`
> 文件名字任意，但是后缀必须是reg注册表文件

然后双击导入`txt.reg`

如果立即查看还是右键没有新建文本文件，那么过会儿再去看就会有了

