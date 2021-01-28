# kubernetes

[toc]

**TODO 每章链接**

## 概念

### Master

**提供集群的管理控制中心。Master组件可以在集群的任何节点上运行。但是通常在一台VM/机器上启动所有的Master组件，并且不会在此VM/机器上运行用户容器**

#### kube-apiserver

**kube-apiserver用于暴露Kubernetes API。任何的资源请求/调用操作都是通过kube-apiserver提供的接口进行。**

#### ETCD

**ETCD是Kubernetes提供默认的存储系统，保存所有集群数据，使用时需要为etcd数据提供备份计划。**

#### kube-controller-manager

**kube-controller-manager运行管理控制器，它们是集群中处理常规任务的后台线程。逻辑上，每个控制器是一个单独的进程，但为了降低复杂性，它们都被编译成单个二进制文件，并在单个进程中运行。**

- *节点(Node)控制器*
- *副本(Replication)控制器：负责维护系统中每个副本中的Pod*
- *端点(Endpoints)控制器：填充Endpoints对象(即连接Services&Pods)*
- *Service Account和Token控制器：为新的Namespace创建默认账户访问API Token*

#### cloud-controller-manager

**云控制器管理器负责与底层云提供商的平台交互。**

- *节点(Node)控制器*
- *路由(Route)控制器*
- *Service控制器*
- *卷(Volume)控制器*

#### kube-scheduler

**kube-scheduler监视新创建没有分配到Node的Pod，为Pod选择一个Node**

#### 插件 addons

**插件(addon)是实现集群Pod和Service功能的。Pod由Deployment/ReplicationController等进行管理。Namespace插件对象是在kube-system Namespace中创建**

#### DNS

**集群DNS是一个DNS服务器，能够为Kubernetes services提供DNS记录。由Kubernetes启动的容器自动将这个DNS服务器包含在它们的DNS searches中**

#### 用户界面

**kube-ui提供集群状态基础信息查看**

#### 容器资源监测

**容器资源监控提供一个UI浏览监控数据**

#### Cluster-level Logging

**负责保存容器日志，搜索/查看日志**

### Node

**提供Kubernetes运行时环境，以及维护Pod**

#### kubelet

**kebelet是主要的节点代理，它会监视已分配给节点的Pod**

- *安装Pod所需的volume*
- *下载Pod的Secrets*
- *Pod中运行的docker容器*
- *定期执行容器健康检查*
- *向系统其它部分报告Pod状态，必要时创建Pod镜像*
- *向系统其它部分报告Node状态*

#### kube-proxy

**kube-proxy通过在主机上维护网络规则并执行连接转发来实现Kubernetes服务抽象**

#### docker

**docker用于运行容器**

#### RKT

**rkt运行容器，作为docker工具的替代方案**

#### supervisord

**supervisord是一个轻量级的监控系统，用于保障kubelet和docker运行**

#### fluentd

**fluentd是一个守护进程，可提供cluster-level logging**

