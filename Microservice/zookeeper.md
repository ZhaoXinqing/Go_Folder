Zookeeper：
    - 是什么？
        - 是一个开源的分布式协调服务，它为分布式应用提供了高效且可靠的分布式协调服务，提供了诸如统一命名空间服务，配置服务和分布式锁等分布式基础服务；

    - 技术特点：
        - 高可用：Zookeeper以集群形态部署，只要集群中大部分机器是可用的（能够容忍一定的机器故障），那么zookeeper本身就仍然是可用的。
        - 高性能：在“读”多于“写”的应用程序中尤其地高性能，因为“写”会导致所有的服务器间同步状态。（“读”多于“写”是协调服务的典型场景。）
        - 顺序访问：对于来自客户端的每个更新请求，ZooKeeper 都会分配一个全局唯一的递增编号，这个编号反应了所有事务操作的先后顺序，应用程序可以使用 ZooKeeper 这个特性来实现更高层次的同步原语。 这个编号也叫做时间戳——zxid（Zookeeper Transaction Id）

    - 系统结构：
        - 引入了Leader、Follower 和 Observer 三种角色
            - Watcher（事件监听器）：是Zookeeper中的一个重要特性。Zookeeper允许用户在指定节点上注册一些Watcher，并且在一些特定事件触发的时候，ZooKeeper服务端会将事件通知到感兴趣的客户端上去，该机制是Zookeeper实现分布式协调服务的重要特性。
            Leader：
            Follower：
    
    - k8s是怎么保证数据一致性？
        - ZAB协议，Paxos算法：
            - ZooKeeper 并没有完全采用 Paxos算法（通用的分布式一致性算法） ，而是使用 ZAB（ZooKeeper Atomic Broadcast 原子广播，一种特别为Zookeeper设计的崩溃可恢复的原子消息广播算法） 协议作为其保证数据一致性的核心算法。基于该协议，ZooKeeper 实现了一种主备模式的系统架构来保持集群中各个副本之间的数据一致性。
            - ZAB 协议两种基本的模式：崩溃恢复和消息广播

    - 相关文章：
        - Zookeeper资源：https://zookeeper.apache.org/doc/r3.6.1/zookeeperOver.html
        - |一篇入魂|Zookeeper入门看这篇就够了：https://blog.csdn.net/jiaodaguan/article/details/103473654