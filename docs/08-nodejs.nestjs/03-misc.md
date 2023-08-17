
## 在 nestjs 中怎样获取用户 ip ？

我的方法：

    const ip = req.headers['x-forwarded-for'] || req.connection.remoteAddress;

就算是通过VPN访问，这个方法仍然可以获得用户真实IP。


## 参考

[how to I get a user's IP address when separate client and server apps, in Node with Nest.js](https://stackoverflow.com/questions/69159038/how-to-i-get-a-users-ip-address-when-separate-client-and-server-apps-in-node-w/76922996#76922996)

[How to get client ip from the request?](https://github.com/nestjs/nest/issues/195)



