---
sidebar_position: 1
title: 入门指南
---

[React-Admin Tutorial](https://marmelab.com/react-admin/Tutorial.html)

创建项目：

    yarn create react-admin test-admin

经过几个提问，配置并创建好项目。

To start working, run cd chat-aishell-io.
Start the app in development mode by running npm run dev.
You can sign in to the application with the following usernames and password:
- janedoe / password
- johndoe / password


# data provider

This uses a third-party package, ra-data-json-server, which maps the JSONPlaceholder API dialect with the react-admin CRUD API.

## 写一个页面组件

参考 ListGuesser 的输出结果（在控制台可以查看到），创建一个文件：src/users.tsx：

```
// in src/users.tsx
import { List, Datagrid, TextField, EmailField } from "react-admin";

export const UserList = () => (
  <List>
    <Datagrid rowClick="edit">
      <TextField source="id" />
      <TextField source="name" />
      <TextField source="username" />
      <EmailField source="email" />
      <TextField source="address.street" />
      <TextField source="phone" />
      <TextField source="website" />
      <TextField source="company.name" />
    </Datagrid>
  </List>
);
```

然后使用上面的组件：

```
// in src/App.tsx
-import { Admin, Resource, ListGuesser, EditGuesser, ShowGuesser } from 'react-admin';
+import { Admin, Resource } from "react-admin";
import { dataProvider } from './dataProvider';
+import { UserList } from "./users";

export const App = () => (
  <Admin dataProvider={dataProvider}>
-   <Resource name="users" list={ListGuesser} />
+   <Resource name="users" list={UserList} />
  </Admin>
);
```


## 编写组件（Composing Components）

List 组件的格式很简单：

    <List>
      {/* children */}
    </List>

`<SimpleList>`组件还挺适合手机端。


## 编写自定义List组件

React-Admin 框架本身就是响应式的，因此手机端使用完全没问题。






## 连接真实API






