# 消息队列

- 定义&特点&使用场景
  - 系统内部通信的核心手段
  - 业务解耦,低耦合、高内聚
  - 保证可靠投递
  - 广播
  - 流量控制/错峰流控
  - 最终一致性

- 设计问题/关键点
  - RPC
  - 高可用
  - 顺序和重复消息
  - 可靠投递
  - 消费关系解析

- 高级话题
  - 批量/异步提高性能
  - pull模型的设计理念
    - 慢消费有优势，consumer按需消费
    - 存在延迟问题，消费方无法准确决定何时拉取消息
  - push模型的设计理念
    - 消息堆积能力和慢消费是平静
    - broker主动向consumer push消息
  - 存储子系统的设计
  - 流量控制的设计
  - 公平调度的实现

- 常用消息中间件
    - ActiveMQ
    - RabbitMQ
      - 遵循AMQP协议,其broker由Exchange、Binding、Queue组成
      - 以broker为中心
      - 有消息确认机制
      - 支持对消息的可靠传递
      - 支持事务
      - 不支持批量操作
    - Kafka
      - 在设计层面上就有丢消息的可能（比如定时刷盘，如果掉电就会丢消息)
      - 遵循一般的MQ结构, producer——broker——consumer
      - 高吞吐量，内部采用消息批量处理
    - MetaQ

- Refs
  - [消息队列设计精要](http://tech.meituan.com/mq-design.html)
  - [Kafka-VS-RabbitMQ](https://www.quora.com/What-are-the-differences-between-Apache-Kafka-and-RabbitMQ)
  
