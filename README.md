# openstack-learn

# 存储
## Openstack与Ceph
* Openstack + Ceph是很多案例，是一种验证过的云计算方案。
* http://www.cnblogs.com/sammyliu/p/4908668.html
  ![screenshot](https://images2015.cnblogs.com/blog/697113/201510/697113-20151025134314958-2128429369.jpg
 "Logo Title Text 1")


# 网络虚拟化
## Why
* 为了云计算，多租户，数据中的虚拟化，突破物理网络的限制，支持大规模的数据中心。

## Open vSwitch
### 历史脉络

* 源自斯坦福的校园网络管理，创建了Nicira公司和Open vSwtich项目，然后，被VMWare收购，后来又将Open vSwitch转交给Linux Foundation来负责维护。VMWare在Open vSwtich的基础上，研发了对应的网络虚拟化商业软件：NSX.
### Open vSwitch 参考资料
* http://blog.51cto.com/virtualelvis/910098
* (历史脉络) https://thenewstack.io/vmware-hands-oversight-open-vswitch-linux-foundation/
* https://dingtongqin.github.io/technology/openvswitch/
## Linux Bridge vs Open vSwtich
* https://kumul.us/switches-ovs-vs-linux-bridge-simplicity-rules/ 在这篇文章中，作者认为，Linux Bridge的简单性胜过Open vSwitch的复杂性。

## 网络基础知识
* NAT: https://wizardforcel.gitbooks.io/network-basic/content/18.html 问题不在于你的理解力不足，而在于你搜索能力和整理能力，第一步是搜索到好的资料，下一步就好办了, 你可能要花很大时间放在找到好资料上，而不是浪费在一些乱七八糟的资料上。
* 看看LAN和TCP/IP的维基百科，你就知道LAN是物理层，链路层的概念，目标就是将**计算机**组织成网络并进行通信；而TCP/IP的目标是**网络**之间的通信，Internet就是Inter Network的简写(https://en.wikipedia.org/wiki/Internetworking)。使用路由器将两个LAN连接起来就是一个最小规模的Internet. 有了这个认识，你就理解VLAN为什么不要IP, VLAN是数据链路层的技术，是LAN层次的技术，而不是Internet的技术。

## RPC
* https://docs.openstack.org/nova/pike/reference/rpc.html

## 超融合

### Nutanix
* Nutanix的核心是NDFS，一个分布式文件系统，CTO领导开发过GFS。所以, NDFS基于GFS的思想专门为虚拟化环境做了设计和优化。
* 基本思想是去掉SAN, 让计算不通过网络(SA)访问存储，以提高性能; NDFS将数据的副本放在不同的节点上，既提供了冗余，又提高了性能（当发生虚拟机迁移，它迁移到的节点上，可能会有数据的副本。）类似，GFS+MapReduce的思想，移动计算逻辑，使其更靠近数据存储位置，提高运算速度。
* 缺点可能是基于副本的存储方式，浪费比较多的空间。
* https://www.virtualtothecore.com/en/nutanix-an-overview-eng/
* https://www.nutanix.com/2014/01/16/chasing-datacenter-efficiency/
* https://www.nutanix.com/press-releases/2012/06/12/nutanix-liberates-nfs-from-the-network-reincarnating-it-as-ndfs/
* http://nutanixbible.com/
  * 用户空间通过一些开发包和驱动程序直接读写存储设备，比通过内核读写，省去了：昂贵的系统调用和中断处理机制，数据复制，上下文切换。发展方向是读写数据的逻辑由内核空间到用户空间发展。基于这个思想，Intel提供了相应的开发包：Storage Performance Development Kit (SPDK).
  * 什么是超融合？1. Natively，converage compute and storage; 2. 不使用专有硬件，使用普通的商用机器。使用软件定义，在这些普通硬件上，构建出企业级产品。专有硬件，就是硬件定义。
  * NDFS与Ceph不同，通过分布式元数据服务来精准控制数据块在系统中的分配位置，以求达到最优的 I/O 性能和稳定性.
* http://www.joshodgers.com/tag/nutanix-distributed-file-system/
* http://www.joshodgers.com/2014/09/26/part-2-problems-with-raid-and-object-based-storage-for-data-protection/
  * NDFS可以更细粒度地恢复数据，基于对象存储的HCI粒度太大，所以性能不好。
* https://www.slideshare.net/Murugesh/nutanix-36050380
* https://www.openstack.org/assets/presentation-media/NutanixOpenStackfortheEnterprise.pptx
* https://www.sdnlab.com/18555.html (这篇文章信息量大，质量高)
  * Cassandra(Medusa): 分布式元数据存储是利用经过大量修改的Cassandra. 利用 Paxos 算法来保证严格一致性。Medusa服务运行在每一个节点上。
  * Zookeeper: 集群配置管理服务Zeus使用了ZooKeeper
  * ProtocolBuffer: Nutanix集群的节点间通讯（包括存储，服务）采用Google的Protocol Buffers以提升分布式系统的通讯效率和性能
  * 也考虑到了3DXPoint的技术。
  * MapReduce: 弹性重复数据删除引擎不仅适用于容量磁盘层 (HDD)，而且适用于性能层（SSD/内存）。在确定重复数据后，依据相同指纹的多个副本，后台进程将使用 DSF MapReduce 框架（管理者）移除重复数据。
  * 有磁盘平衡技术，
  * 没有专有网络。都是走的标准10GbE网络.
  * 技术上，没有集群扩展节点限制。
  * 也可以部署为Storage-Only. 
## Some tips
* How to know if the linux you are using is a VM in openstack. 
```shell
sudo dmidecode  | grep -i OpenStack
        Manufacturer: OpenStack Foundation
        Product Name: OpenStack Nova
```


# 参考
## 网络:
* https://goyalankit.com/blog/linux-bridge
* http://www.cnblogs.com/sammyliu/p/4622563.html
* http://www.cnblogs.com/sammyliu/p/4622563.html
× http://blog.51cto.com/virtualelvis/910098
* https://dingtongqin.github.io/technology/openvswitch/
