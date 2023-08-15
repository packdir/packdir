# dist 和 lib 目录有何不同？

dist 目录通常是用于发布 UMD，用户可以直接使用它，而不不需要通过包管理器。

lib 通常是 package.json main 指向的位置，用户通过 npm 安装的时候就是使用该目录下的内容。一个包的源代码通常在 src 目录下，编译之后保存到 lib 目录下，可以供用户安装使用。


## 参考

UMD 文章参考：

- [What are UMD modules? One final module system to rule them all](https://jameshfisher.com/2020/10/04/what-are-umd-modules/)

- [What the heck are CJS, AMD, UMD, and ESM in Javascript?](https://dev.to/iggredible/what-the-heck-are-cjs-amd-umd-and-esm-ikm)

- [学习UMD](https://github.com/cumt-robin/umd-learning)


