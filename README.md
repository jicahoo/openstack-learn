# openstack-learn


# 网络虚拟化
## Why
* 为了云计算，多租户，数据中的虚拟化，突破物理网络的限制，支持大规模的数据中心。

## Open vSwitch
### 历史脉络

* 源自斯坦福的校园网络管理，创建了Nicira公司和Open vSwtich项目，然后，被VMWare收购，后来又将Open vSwitch转交给Linux Foundation来负责维护。
### Open vSwitch 参考资料
* http://blog.51cto.com/virtualelvis/910098
* (历史脉络) https://thenewstack.io/vmware-hands-oversight-open-vswitch-linux-foundation/
* https://dingtongqin.github.io/technology/openvswitch/
## Linux Bridge vs Open vSwtich
* https://kumul.us/switches-ovs-vs-linux-bridge-simplicity-rules/ 在这篇文章中，作者认为，Linux Bridge的简单性胜过Open vSwitch的复杂性。

## 网络基础知识
* NAT: https://wizardforcel.gitbooks.io/network-basic/content/18.html 问题不在于你的理解力不足，而在于你搜索能力和整理能力，第一步是搜索到好的资料，下一步就好办了, 你可能要花很大时间放在找到好资料上，而不是浪费在一些乱七八糟的资料上。


## RPC
* https://docs.openstack.org/nova/pike/reference/rpc.html


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
