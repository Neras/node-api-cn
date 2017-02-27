
There are four fundamental stream types within Node.js:

* [Readable][] - streams from which data can be read (for example
  [`fs.createReadStream()`][]).
* [Writable][] - streams to which data can be written (for example
  [`fs.createWriteStream()`][]).
* [Duplex][] - streams that are both Readable and Writable (for example
  [`net.Socket`][]).
* [Transform][] - Duplex streams that can modify or transform the data as it
  is written and read (for example [`zlib.createDeflate()`][]).


在Node.js里面stream有四种基本类型：

* `Readable` - 从数据中得到的流是能够被读的（举例：[fs.createReadStream()](http://nodejs.cn/api/fs.html#fs_fs_createreadstream_path_options)）
* `Writeable` - 传输的数据流是可以被写的（举例：[fs.createWriteStream()](http://nodejs.cn/api/fs.html#fs_fs_createwritestream_path_options))
* `Duplex`(表示两种状态都可以) - 流可以同时是可读和可写的（举例：[net.Socket](http://nodejs.cn/api/net.html#net_class_net_socket))
* `Transform`（应该表示 可变化的） - 存在`Duplex`状态（同时可读又可写状态）的流就像是同时可读和可写一样能够修改或者改变的。（举例：[zlib.createDeflate()](http://nodejs.cn/api/zlib.html#zlib_zlib_createdeflate_options) )

