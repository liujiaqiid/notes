# Ali云数据库 MongoDB 版

### 服务调研

- 采用三节点副本集的高可用架构，容灾切换，故障迁移完全透明化
- 读写分离
- IP白名单设置
- DDOS防护
- 对数据库性能有比较详细的监控
- 支持数据迁入迁出操作


### 问题

- 有必要使用独立备份机制, 可采用OSS服务 + 备份策略 ??
```
阿里协议： "数据备份系您的义务和责任。虽然阿里云的云数据库MongoDB版可能会配置具有日常数据备份功能的工具，但并不意味着数据备份是阿里云的义务。阿里云不保证完全备份用户数据，亦不对用户数据备份工作或结果承担任何责任."
```
- 是否打开慢查询日志？？
```
云数据库MongoDB版会将每个DB上处理时间超过100ms的请求记录到db.system.profile集合中
```
- 能否使用mongodb的oplog？？？？
- 配置升级过程中会出现30s内的闪断，主备可能发生切换,需要提前做好准备
- 不支持外网直接访问
  - 方案一, 使用某一台ECS服务器+rinetd做请求转发，达到外网可访问的状态
  - 方案二, 创建RAM子账户,让用户通过子账户在web端管理

mongo --host 1.1.1.1:3717 -u root -p 密码 --authenticationDatabase admin

- 目前暂时不支持分片操作sharding

- 开发人员配置问题

- 运维/测试 人员操作问题



### Refs  
- [公网连接云MongoDB解决方案](https://help.aliyun.com/knowledge_detail/39952.html?spm=5176.7839947.2.7.nR6pex)
- [RAM阿里云资源权限控制](https://help.aliyun.com/document_detail/28627.html)
