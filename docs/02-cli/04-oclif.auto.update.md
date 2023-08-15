


官方文档语焉不详：[Autoupdater](https://oclif.io/docs/releasing/#autoupdater)


1. 安装

    npm i @oclif/auto-update

    或者：

    yarn add @oclif/auto-update

2. 修改 package.json，增加：

    "oclif":
    {
      "plugins":
      {
        "@oclif/auto-update"
      }
    }

但是，上述安装完成后，使用 update 命令，得到的结果是“not updatable”。

这里的 [issue](https://github.com/oclif/plugin-update/issues/379) 反映了这个问题。

