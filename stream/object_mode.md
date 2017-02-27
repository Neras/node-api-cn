
All streams created by Node.js APIs operate exclusively on strings and `Buffer`
objects. It is possible, however, for stream implementations to work with other
types of JavaScript values (with the exception of `null`, which serves a special
purpose within streams). Such streams are considered to operate in "object
mode".

Stream instances are switched into object mode using the `objectMode` option
when the stream is created. Attempting to switch an existing stream into
object mode is not safe.

所有由Node.js创建的流仅仅是用来操作字符串和`Buffer`对象的。但是对流的实现来说，它也能够应用到其他类型的JavaScript值（但是`null`除外，它在流里面有特殊的用途）。这样的流操作被认为是"对象模式（Object mode）"。

当流被创建时，流的实例被切换到使用`objectMode`设置的对象模式（object mode）。企图将一个已经出现的流切换到对象模式是不安全的。