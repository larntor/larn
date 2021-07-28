当使用cx_oracle模块执行sql查询时，一旦执行卡住，超时该怎么处理？这里介绍通过使用oracle自带方式来处理。通过sqlnet.ora文件，配置SQLNET.RECV_TIMEOUT参数来实现。
这个参数在客户端设置的作用是，其发起的请求，必须在设置值内有返回，否则报错中断。

可以在python客户端上的oracle目录文件下添加sqlnet.recv_timeout=3属性，
然后通过下面sql测试
                            begin
                            dbms_lock.sleep(10);
                            end;
可以看到捕捉到的异常如下
