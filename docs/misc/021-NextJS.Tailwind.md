
## 安装

使用命令安装：

    npx create-next-app@latest

输入名字，其他都用默认选项。

测试：

    npm run dev


## 部署

编译：

    npm run build

修改port（可选），修改 package.json:

    "start": "   -p 3001"

启动：

    npm run start


## Routing

从13版本开始，推荐使用 app routing，它与之前的 pages routing 可以同时使用。

默认情况下，app 目录下使用服务端组件，当然也可以使用客户端组件。关于服务端组件，详见[Server Components](https://nextjs.org/docs/app/building-your-application/rendering/server-components)

在app目录下：

- 文件夹作为route
- 文件创建UI

可以在app目录下放置其他文件，但只有以下两个文件存在之一，该目录才会routing：

- page.js
- route.js


## src

可以把 app, pages, components, lib 等文件夹放到src目录下，根目录下只保存配置文件。src目录说明详见：[src Directory](https://nextjs.org/docs/pages/building-your-application/configuring/src-directory)


