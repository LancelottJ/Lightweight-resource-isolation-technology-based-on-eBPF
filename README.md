# 基于eBPF的轻量化资源隔离技术

## 题目

使用eBPF在Linux内核实现对CPU、Memory、Disk I/O和Network I/O等资源的控制。基本实现cgroup对上述资源的各种约束功能

## 项目描述

#### 容器隔离机制

服务器无感知计算平台需要为用户并发启动大量函数实例来响应用户的业务需求，而且不同函数对资源的使用是随着时间不断变化的，并发函数间会因竞争共享的内核资源而导致性能下降，需要以函数为粒度对资源的使用进行精确的监控。以此为基础，对用户的资源访问请求进行约束，保证函数间不会出现资源的抢占行为。

当前函数通常运行在独立的容器中，而容器依靠内核中的cgroup来实现对资源的隔离。已有研究表明，在高并发情况下，大量函数实例同时启动，函数运行容器的cgroup初始化开销会急剧增长。

为此，需要在操作系统内核层实现资源的轻量级控制，降低开销。考虑到云计算中资源的种类繁复多样，并需要设计用户可定义的隔离接口，方便开发者对更多的内核资源进行隔离。

#### eBPF技术

eBPF技术，在用户程序触发系统调用时注入预定义的代码，动态聚合分析函数行为，并对非法操作进行控制。该技术是目前热门的内核可编程机制，提供多语言无侵入的观测能力，兼具高性能高扩展特性，生态发展很好，未来前景广大，但当前其主要集中在网络性能优化和安全领域。

我们创新性将其应用到服务器无感知计算的资源隔离中，为函数提供轻量级的隔离机制，有利于后期的技术落地和社区推广。

#### 赛题要求

本赛题拟基于eBPF技术实现轻量化的、用户可定义的内核资源隔离机制，降低初始化的开销，提高高并发下函数沙箱的启动速度。

## 所属赛道

2023全国大学生操作系统比赛的“OS功能设计”赛道

## 参赛要求

- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生（2023年春季学期或之后本科毕业的大一~大四的
  学生）
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖 
- 请遵循“2023全国大学生操作系统比赛”的章程和技术方案要求

## 难度

高级

## 项目导师

樊浩 haofan@hust.edu.cn

## 预期目标

- 目标一：实验测试现有cgroup、namespace机制的并发性能

- 目标二：基于eBPF实现对disk io、network io资源的约束

- 目标三：基于eBPF实现对CPU、Memory资源的约束

### License

- [GPL-2.0](https://opensource.org/licenses/GPL-2.0)

