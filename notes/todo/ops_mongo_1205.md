# Mongodb

- 现象: 当文档数组大于128时, 可能照成mongod进程crash.
- 解决方案: Mongodb版本问题 2.6.0 ——> 2.6.1

- Refs
  - [Array updates on documents with more than 128 BSON elements may crash mongod](https://jira.mongodb.org/browse/SERVER-13516?jql=project%20%3D%20SERVER%20AND%20fixVersion%20%3D%20%222.6.1%22%20AND%20text%20~%20%22segmentation%20fault%22)
