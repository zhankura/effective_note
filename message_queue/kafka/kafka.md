# 整体架构
---
## 1. 推拉模式优缺点
## 2. 动态重平衡
* 解决动态组成员资源分配的问题
* Group Member Protocol 负责组成员的管理
    * 主要在broker上实现的
    * JoinGroup SyncGroup HeartBeat LeaveGroup
    * 接收到消费者的JoinGroup请求会hold一段时间，如果期间内消费者数量未发生变化，开始动态重平衡。选第一个Join的作为Leader，分配不同的分区，通过SyncGroup同步这个分区信息。消费者定期发送HeartBeat表明自己存活
* Conusmer Embeded Protocol 分区分配
    * 主要在客户端实现
* 协调者 对应一个消费者组
* Stop The World 有消费者需要更新时，所有消费者都会通过HeartBeat的回应得知该停止消费
* Static Membership
* Incremental Cooperative Rebalancing
## 3. zookeeper
## 4. 服务发现
## 5. lag堆积报警