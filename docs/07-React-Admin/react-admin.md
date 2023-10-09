
指南：
[React-Admin Tutorial](https://marmelab.com/react-admin/Tutorial.html)



## Data providers

第三方后端：
[Supported Data Provider Backends](https://marmelab.com/react-admin/DataProviderList.html)


### Simple REST Data Provider

从这个最基本的REST接口开始学习：[simple rest](https://github.com/marmelab/react-admin/tree/master/packages/ra-data-simple-rest)

安装：

    npm i ra-data-simple-rest



## Writing a Data Provider

写一个后端，学习接口标准写法：
[Writing A Data Provider](https://marmelab.com/react-admin/DataProviderWriting.html)


### 请求

RA 请求包括三要素：

- 方法，如 getList, getOne 等等。
- 资源，如 articles 等等。
- 参数

对比 HTTP，下面是 HTTP 请求要素：

- 动词（GET, POST, ...）
- url
- headers
- body

RA 请求例子：

```
dataProvider.getList('posts', {
    pagination: { page: 1, perPage: 5 },
    sort: { field: 'title', order: 'ASC' },
    filter: { author_id: 12 },
});

dataProvider.getOne('posts', { id: 123 });

dataProvider.getMany('posts', { ids: [123, 124, 125] });

dataProvider.getManyReference('comments', {
    target: 'post_id',
    id: 123,
    sort: { field: 'created_at', order: 'DESC' }
});

dataProvider.create('posts', { data: { title: "hello, world" } });

dataProvider.update('posts', {
    id: 123,
    data: { title: "hello, world!" },
    previousData: { title: "previous title" }
});

dataProvider.updateMany('posts', {
    ids: [123, 234],
    data: { views: 0 },
});

dataProvider.delete('posts', {
    id: 123,
    previousData: { title: "hello, world" }
});

dataProvider.deleteMany('posts', { ids: [123, 234] });
```
