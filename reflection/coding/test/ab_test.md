## 性能测试

### AB压力测试

ab -n 100 -c 1000 

* -n 并发连接数100 C
* -c 1000 总请求数 R

假设总耗时为T, 关键指标计算

* QPS = R / T
* RT = T / (R/C)

性能评判：

* 并发数一定的情况下，QPS越高，RT低，服务器性能越好
* 注意RT，计算的是单个连接的RT，因此请求基数要除以并发连接数，得到单个连接的总请求数
* 计算RT时并不关心服务器的cpu和线程模型，单个连接下，多核多线程模型下同一时刻能处理多个请求，从而降低单个请求的RT。但是如果多个请求是来自多个连接，计算RT时还要除以连接数。这里要区分并发连接数和并发请求数。

### 关于并发数

所谓并发数，这是一个前提，我们关注的是不同并发数下的QPS和延时

一般收到网络延迟的影响，服务端并发 远小于 客户端并发，测试的时候，保证测试客户端和服务端在一个LAN，可以保证客户端并发≈服务端并发

相同并发下，服务器用不同的线程或进程模型来处理，会导致QPS或RT不同
