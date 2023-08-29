

当 Node.js 收到请求，然后使用 reponse 对象来响应。reponse 对象是可写流，因此可以在服务器端进行写入。

下面两个例子是 ChatGPT 给出的例子：

下面是使用流来连接文件的例子：

```
const http = require('http');

const server = http.createServer((req, res) => {
  const fileStream = fs.createReadStream('index.html');

  fileStream.pipe(res);
});

server.listen(3000, () => {
  console.log('Server listening on port 3000');
});
```


下面是使用流来连接数据库的例子：

```
const http = require('http');
const mongodb = require('mongodb');

const server = http.createServer((req, res) => {
  const client = new mongodb.MongoClient('mongodb://localhost:27017');

  client.connect((err, db) => {
    if (err) {
      return res.send(500, err);
    }

    const collection = db.collection('products');

    collection.find({}, (err, results) => {
      if (err) {
        return res.send(500, err);
      }

      const resultsStream = results.stream();

      resultsStream.pipe(res);
    });
  });
});

server.listen(3000, () => {
  console.log('Server listening on port 3000');
});
```




## 参考

[OpenAI Completion Stream with Node.js and Express.js](https://stackoverflow.com/questions/76137987/openai-completion-stream-with-node-js-and-express-js)

[Use Streams to Build High-Performing Node.js Applications](https://blog.appsignal.com/2022/02/02/use-streams-to-build-high-performing-nodejs-applications.html)

[Node.js Streams: Everything you need to know](https://www.freecodecamp.org/news/node-js-streams-everything-you-need-to-know-c9141306be93/)




