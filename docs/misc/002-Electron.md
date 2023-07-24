---
title: Electron
---

Electron 使用 Chromium 和 Node.js 来创建跨平台桌面应用。

[Electron Fiddle](https://electronjs.org/fiddle)是运行Electron的工具，可以用来做实验环境。


## Quick Start

首先，创建一个 NodeJS 项目：

    mkdir e1 && cd e1
    npm init

要求：

- 入口文件为 main.js
- author, description 要有内容

然后，安装 Electron：

    npm i -D electron

在 package.json 中增加 start 命令：

    "scripts": {
      "start": "electron ."
    },

创建空文件 main.js:

创建文件 index.html:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <!-- https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP -->
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self'">
    <title>Hello World!</title>
  </head>
  <body>
    <h1>Hello World!</h1>
    We are using Node.js <span id="node-version"></span>,
    Chromium <span id="chrome-version"></span>,
    and Electron <span id="electron-version"></span>.
  </body>
</html>
```

为了加载这个页面，需要两个模块：

- The **app** module, which controls your application's event lifecycle.
- The **BrowserWindow** module, which creates and manages application windows.



## 发布

使用 Electron Forge 打包和发布应用，详细指南见 [Forge 文档](https://www.electronforge.io/)。

### 打包

安装  Electron Package 模块，Electron Packager is a command line tool and Node.js library that bundles Electron-based application source code with a renamed Electron executable and supporting files into folders ready for distribution.

    npm install electron-packager -g

打包：

    electron-packager . --platform=win32 --arch=x64 MYAPP

打包后的文件在 MYAPP-win32-x64 目录下。

### 安装 WiX

安装 [WiX Toolset](https://github.com/wixtoolset/wix3/releases)，用于创建 Windows 安装程序。









打包时，要指定 icon 文件：

    icon = path.join(__dirname, 'assets/icons/png/64x64.png')



