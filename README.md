# openstack 完整部署流程

author：t1ngyx

考虑到这个部署到实现复杂度并不是三个本科阶段的大学生可以实现的，本文档意在推出一个极简部署流程。

## 安装流程

1. 从百度网盘链接中下载单节点

> 通过网盘分享的文件：单节点
> 链接: https://pan.baidu.com/s/1Vmh3zvYT2REOjCMT9ZBYsg?pwd=1145 提取码: 1145 
> --来自百度网盘超级会员v6的分享

2. 里面有三个压缩包

> controller.zip // 控制节点
>
> cinder.zip // 管理节点
>
> compute.zip // 计算节点

小组三人只需要下载其中一个，分工好！！！

3. 解压在一个存储空间 $> 20G$ 的文件夹中命名尽量不用中文

4. 双击里面的.vmx文件，点击获取所有权

5. 点击VMware左上角编辑打开虚拟网络编辑器

6. 把桥接模式的网卡设置好

   <img src="/Users/apple/Downloads/{9EE766EB-2270-4e78-9F12-6CDEC949FF7C}.png" alt="{9EE766EB-2270-4e78-9F12-6CDEC949FF7C}" style="zoom:50%;" />



7. 应用即可

## 部署流程

1. 三台电脑链接同一个iPhone的热点，一定得是iPhone，其他热点的网段不一样会出问题
2. 注意好三台电脑的ip地址，不可以是172.20.10.2或172.20.10.3或172.20.10.5，否则自行修改静态ip
3. 三人分别启动虚拟机，账户root 密码000000
4. 三台启动成功后访问172.20.10.2/dashboard为控制面板
5. 域default 账户admin 密码admin
6. controller 执行 

> systemctl start httpd
>
> source /etc/keystone/admin-openrc

6. 所有节点执行

> systemctl restart openstack* 

7. 至此云计算节点全部部署成功
8. cinder节点和controller节点执行

> systemctl status openstack-cinder-volume

确保显示的是actived否则执行

> systemctl restart openstack-cinder-volume



