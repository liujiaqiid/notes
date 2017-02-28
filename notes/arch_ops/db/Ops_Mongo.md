# Mongodb

#### MongoDB Crash @ 2016-12-05
- 现象: 当文档数组大于128时, 可能照成mongod进程crash.
- 解决方案: Mongodb版本问题 2.6.0 ——> 2.6.1

- Refs
  - [Array updates on documents with more than 128 BSON elements may crash mongod](https://jira.mongodb.org/browse/SERVER-13516?jql=project%20%3D%20SERVER%20AND%20fixVersion%20%3D%20%222.6.1%22%20AND%20text%20~%20%22segmentation%20fault%22)

#### MongoDB Connection Error
- 使用mongo shell连接实例时，提示类似如下的错误：
```
  2015-12-21T10:20:36.084+0800 I NETWORK  Socket recv() errno:54 Connection reset by peer  1.2.3.4:27017

  2015-12-21T10:20:36.087+0800 I NETWORK  SocketException: remote: 1.2.3.4:27017 error: 9001 socket exception [RECV_ERROR] server [1.2.3.4:27017]

  2015-12-21T10:20:36.087+0800 I NETWORK  DBClientCursor::init call() failed
```  
  上述错误信息说明是server端主动断开了连接，原因是该实例的连接数已经达到上限，无法再新建网络连接。


#### 强制终端某个请求

db.currentOp()找出一直没结束的请求的opid（currentOp.opid字段)，然后db.killOp(opid)来杀掉对应的请求。
