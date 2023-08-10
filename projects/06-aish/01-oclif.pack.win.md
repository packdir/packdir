
## 准备工作

在 package.json 中增加命令：

    "scripts": {
      "postinstall": "ts-node ./bin/postinstall.js",
    }

postinstall.js 脚本的作用是将 Windows 版本的 node_sqlite3.node 文件复制到指定目录。

接下来就新增两个文件：

    bin/node_sqlite3.node
    bin/postinstall.js


## 打包

使用下面的命令打包 Windows 版本：

    oclif pack win




