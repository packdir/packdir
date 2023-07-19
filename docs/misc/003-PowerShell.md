


## 查看环境变量

列出环境变量 Path：

    PS C:> cd env:
    PS Env:> ls path

通常 Path 内容很长，上面的命令并没有显示全部内容，只显示一行的长度内容。

使用下面的命令来查看 Path 全部内容：

    PS Env:\> (ls path).value

如果要看得更清楚，一个路径一行显示，可以使用下面的命令：

    PS Env:\> (ls path).value.split(“;”)
    C:\Python311\Scripts\
    C:\Python311\
    C:\Python39\Scripts\
    C:\Python39\
    C:\windows\system32
    C:\windows
    D:\Program Files\Git2\cmd
    C:\windows\System32\Wbem
    C:\windows\System32\WindowsPowerShell\v1.0\
    C:\windows\System32\OpenSSH\
    ...



