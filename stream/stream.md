
> Stability: 2 - Stable

A stream is an abstract interface for working with streaming data in Node.js.
The `stream` module provides a base API that makes it easy to build objects
that implement the stream interface.

There are many stream objects provided by Node.js. For instance, a
[request to an HTTP server][http-incoming-message] and [`process.stdout`][]
are both stream instances.

Streams can be readable, writable, or both. All streams are instances of
[`EventEmitter`][].

The `stream` module can be accessed using:

```js
const stream = require('stream');
```

While it is important for all Node.js users to understand how streams work,
the `stream` module itself is most useful for developers that are creating new
types of stream instances. Developer's who are primarily *consuming* stream
objects will rarely (if ever) have need to use the `stream` module directly.

> 稳定性：2 - 稳定的

Stream 是在Node.js中为了处理流数据(streaming data)的一个抽象接口。`stream`模块提供了一个能够轻松构建实现 Stream接口的对象的基础API。

Node.js提供了较多stream对象。比如：[对HTTP服务的request](http://nodejs.cn/api/http.html#http_class_http_incomingmessage)和[process.stdout](http://nodejs.cn/api/process.html#process_process_stdout)都是stream的实例（原文为 stream instances，但感觉译作引用比较好）。

流可以是可读的，可写的，或者同时是可读和可写的。所有的流都是[EventEmitter](http://nodejs.cn/api/events.html#events_class_eventemitter)的实例。

`stream`模块可以这样被引用：

```JavaScript
const stream = require('stream');
```

`stream`模块自身能够创建很多类型的stream引用，对开发者来说是非常有用的，但是同时对所有Node.js用户来说，理解流的工作原理也是非常重要的。对主要使用stream对象的开发者来说，很难得（或者说几乎从不）需要直接使用`stream`模块。