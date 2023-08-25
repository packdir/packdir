
[Node.js官方文档：Stream](https://nodejs.org/api/stream.html#stream_stream)


当处理大文件时，比如要发送一个长视频文件给客户端，通常不会将这个大文件放到相应中，因为太大了，会占用过多的内存。通常会使用流式（stream）响应的方式来处理，流式响应将数据分块（chunk）分别处理。

在 Node.js 中，流式是内建的功能。流用于处理流式数据，流式数据一次到底一个块，而且是异步到达。

In Node.js streams are used in many built-in modules to handle async data processing, for example, the http module uses streaming interfaces with ClienRequest and ServerResponse. Stream data is a buffer by default, unless it is configured to with objects. This means it helps to buffer the data in memory.

这里的概念：buffer

流式数据除了节约空间和时间，还有一个优势是可以组合，一个输入出流可以作为另一个输入流，这样使用管道方式将流组合起来。

四种流类型：

1. Writable. 例如：fs.createWriteStream()
2. Readable. 例如： fs.createReadStream()
3. Duplex. 例如： net.Socket
4. Transform. 类似于 Duplex，但是流数据可以被修改。例如： zlib.createDeflate()

所有的流都是 EventEmitter 的实例，但是不推荐在流式中直接处理事件，最好是使用 pipe 和 pipeline 方法。但是了解与流相关的事件，有助于更好的控制流的处理，比如在流创建和结束的时候插入处理。

可读流的事件有：

- data - emitted when the stream outputs a data chunk.

- readable - emitted when there is data ready to be read from the stream.

- end - emitted when no more data is available.

- error - emitted when an error has occurred within the stream, and an error object is passed to the handler. Unhandled stream errors can crash the application.

可写流的事件有：

- drain will be emitted, when the writable stream's internal buffer has been cleared and is ready to have more data written into it.

- finish will be emitted, when all data has been written.

- error will be emitted when an error occurred while writing data, and an error object is passed to the handler. Unhandled stream errors can crash the application.



