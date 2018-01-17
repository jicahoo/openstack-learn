# openstack-learn


# 网络虚拟化
## Why
* 为了云计算，多租户，数据中的虚拟化，突破物理网络的限制，支持大规模的数据中心。

## Open vSwitch
### 历史脉络
* https://thenewstack.io/vmware-hands-oversight-open-vswitch-linux-foundation/
* 源自斯坦福的校园网络管理，创建了Nicira公司和Open vSwtich项目，然后，被VMWare收购，后来又将Open vSwitch转交给Linux Foundation来负责维护。
## Linux Bridge


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
