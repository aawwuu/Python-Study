操作系统：	CentOS 7.4

IP Address：	10.10.11.42/24

OpenStack：	Pike



关闭防火墙和 selinux

```shell
[root@openstack ~]# systemctl stop firewalld && systemctl disable firewalld
……
[root@openstack ~]# getenfooce
Disabled
```

设置主机名解析

```shell
[root@openstack ~]# hostname
openstack
[root@openstack ~]# cat /etc/hosts
127.0.0.1  localhost localhost.localdomain localhost4 localhost4.localdomain4

10.10.11.42	openstack
```

不要使用 NetworkManager

```shell
[root@openstack ~]# systemctl stop NetworkManager && systemctl disable NetworkManager
[root@openstack ~]# cat /etc/sysconfig/network-scripts/ifcfg-eth0 
DEVICE=eth0
IPADDR=10.10.11.42
NETMASK=255.255.255.0
NETWORK=10.10.11.0
GATEWAY=10.10.11.1
ONBOOT=yes
NAME=eth0
```

配置源，使用官方源，或者配置内部源

```shell
[root@openstack ~]# yum update -y
[root@openstack ~]# yum install -y https://www.rdoproject.org/repos/rdo-release.rpm
```

安装 OpenStack PackStack

```shell
[root@openstack ~]# yum install -y openstack-packstack
```

生成 answer file，answer file 是安装 OpenStack 的模板文件

```shell
[root@openstack ~]# packstack --gen-answer-file=/root/answer.txt
```

编辑 answer file，选择安装哪些组件

安装 OpenStack,安装完成后会提示

```shell
[root@openstack ~]# packstack --answer-file /root/answer.txt
……
**** Installation completed successfully ****
```
