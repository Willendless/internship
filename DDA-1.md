# *Designing Data-Intensive Applications*

## ch1

### goal: what we're actually trying to achieve

+ *reliability*: fault tolerant/resilient
  + hardware faults：随机且若相关的
  + software errors：相关的且难处理的
  + operator errors：配置错误，不可避免的
+ *scalability*: handle load increased
  + 描述负载: *load parameters*
    + 例如：twitter中每个user的follower数量是load parameter
  + 描述性能:
    + 增加load parameter保持系统资源不变，系统性能会受到怎样的影响
    + 增加load parameter，如何增加资源以使系统性能不变
    + 示例：
      1. hadoop批处理系统，*吞吐量：*单位时间处理的记录数
      2. 在线系统，*响应时间：*客户端发出请求到接收到响应的时间
          + 注：区分响应时间和延迟的概念，*延迟*指的是请求等待被处理的时间。
          + 单次响应时间的统计结果通常没有意义，需要考虑响应时间的分布
            + 通过百分比描述响应时间的统计结果（中位数是50%，简写为p50，其它常见的还有p95，p99，p999）
            + 高比例百分比响应时间被称为尾延迟：响应时间最慢的请求通常是数据最多的也即最重要的用户
            + 响应时间百分比通常用于*service level objectives（slo）*或者*service level agreements（sla）*的定义
              + 例如：一个sla要求服务p50小于200ms，而p99小于1s，同时至少99.9%的时间满足该约束
            + *尾延迟放大：*单个用户请求需要执行多个后端调用，即使只有少量后端调用较为缓慢，仍会导致大多数用户请求缓慢。
  + 如何应对负载增加
    + 水平扩展
    + 垂直扩展
+ *maintainability*设计原则
  + operability: 监控，文档，维护。
  + simplicity：通过好的抽象，将大规模系统中良定义的，可重用的组件提取出来。
  + evolvability：敏捷开发，TDD、重构
