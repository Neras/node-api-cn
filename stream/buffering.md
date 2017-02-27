
<!--type=misc-->

Both [Writable][] and [Readable][] streams will store data in an internal
buffer that can be retrieved using `writable._writableState.getBuffer()` or
`readable._readableState.buffer`, respectively.

The amount of data potentially buffered depends on the `highWaterMark` option
passed into the streams constructor. For normal streams, the `highWaterMark`
option specifies a total number of bytes. For streams operating in object mode,
the `highWaterMark` specifies a total number of objects.

Data is buffered in Readable streams when the implementation calls
[`stream.push(chunk)`][stream-push]. If the consumer of the Stream does not
call [`stream.read()`][stream-read], the data will sit in the internal
queue until it is consumed.

Once the total size of the internal read buffer reaches the threshold specified
by `highWaterMark`, the stream will temporarily stop reading data from the
underlying resource until the data currently buffered can be consumed (that is,
the stream will stop calling the internal `readable._read()` method that is
used to fill the read buffer).

Data is buffered in Writable streams when the
[`writable.write(chunk)`][stream-write] method is called repeatedly. While the
total size of the internal write buffer is below the threshold set by
`highWaterMark`, calls to `writable.write()` will return `true`. Once
the size of the internal buffer reaches or exceeds the `highWaterMark`, `false`
will be returned.

A key goal of the `stream` API, particularly the [`stream.pipe()`] method,
is to limit the buffering of data to acceptable levels such that sources and
destinations of differing speeds will not overwhelm the available memory.

Because [Duplex][] and [Transform][] streams are both Readable and Writable,
each maintain *two* separate internal buffers used for reading and writing,
allowing each side to operate independently of the other while maintaining an
appropriate and efficient flow of data. For example, [`net.Socket`][] instances
are [Duplex][] streams whose Readable side allows consumption of data received
*from* the socket and whose Writable side allows writing data *to* the socket.
Because data may be written to the socket at a faster or slower rate than data
is received, it is important for each side to operate (and buffer) independently
of the other.

不管是可写还是可读的流数据都会储存在一个内部的缓冲区域，在这个缓冲区里面能够分别使用`writable._writableState.getBuffer()`或者`readable.__readableState.buffer()`来重新获取。

潜在缓冲的数据量取决于传递到流的构造函数的`highWaterMark`的设置。对普通的流来说，`highWaterMark`的设置特指一定数量的字节。对于在对象模式中操作的流来说，`highWaterMark`的设置特指一定数量的对象。

