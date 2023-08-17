

## nestjs 错误处理流程

1. When a fetch is triggered (usually coming from the data provider), if an error happen, it is caught and transformed into an HttpError and re-thrown (source)

2. In the process, the HTTP Error message becomes either the json.message or the response statusText. It's here that a 422 HTTP Error becomes Unprocessable Entity (source)

3. Then the error is caught again at a higher level to be transformed into a redux action. (source)

4. Finally, the error is transformed into a notification containing the error message.

来源：[Show API error in notification](https://stackoverflow.com/q/52010432/3054511)



## 在 nestjs 中怎样获取用户 ip ？

我的方法：

    const ip = req.headers['x-forwarded-for'] || req.connection.remoteAddress;

就算是通过VPN访问，这个方法仍然可以获得用户真实IP。


### 参考

[how to I get a user's IP address when separate client and server apps, in Node with Nest.js](https://stackoverflow.com/questions/69159038/how-to-i-get-a-users-ip-address-when-separate-client-and-server-apps-in-node-w/76922996#76922996)

[How to get client ip from the request?](https://github.com/nestjs/nest/issues/195)



