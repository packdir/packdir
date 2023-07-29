

[Release](https://oclif.io/docs/releasing)

有两种方式发布命令行程序：

1. npm

2. 二进制安装包

Windows:

    oclif pack win


## 单独二进制包(standalone tarballs)

注意！！！

> oclif 3 版本打包需要7z！！！
> 在Ubuntu下安装7z：
>     sudo apt install p7zip-full p7zip-rar
>
> 没有安装7z的话，使用 oclif pack win 命令，打包不会结束，也没有错误提示，要命！！！


在根目录使用下面命令进行打包：

    oclif pack tarballs

打包将把node二进制环境打包进去，因此用户不需要安装node也可以使用。

打包文件在这里：

    dist/

