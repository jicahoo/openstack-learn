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
* Nutanix的核心是NDFS，一个分布式文件系统，开发者开发过GFS.
* https://www.nutanix.com/press-releases/2012/06/12/nutanix-liberates-nfs-from-the-network-reincarnating-it-as-ndfs/
* http://nutanixbible.com/
* http://www.joshodgers.com/tag/nutanix-distributed-file-system/
* https://www.slideshare.net/Murugesh/nutanix-36050380
* https://www.openstack.org/assets/presentation-media/NutanixOpenStackfortheEnterprise.pptx

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
