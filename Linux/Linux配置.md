# 账户信息
 - Linux账号
   - root用户 
       - root
       - root1234
   - 普通用户
      - normal
      - normal1234
 - MySQL账号
    - root用户
      - root
      - 123456
    - 普通用户
      - demo
      - 123456

# 网络配置
 1. 编辑网络配置文件 
      - **vi /etc/sysconfig/network-scripts/ifcfg-ens33**
      - 修改
         - BOOTPROTO=”static” #静态连接
         - ONBOOT=”yes” #网络设备开机启动 
      - 添加
         - IPADDR=”192.168.80.128 #192.168.59.x, x为128~254.
         - NETMASK=”255.255.255.0” #子网掩码
         - GATEWAY=”192.168.80.2” #网关IP
 2. 配置dns
      - **vi /etc/resolv.conf**
      - 添加
         - nameserver 8.8.8.8
         - nameserver 8.8.4.4
 3. 查看网络配置是否正确
      - **ip addr**
 4. 重启网络服务
      - **systemtcl restart network.service**
 5. 测试
      - **ping www.baidu.com**

 - 参考
   - > [静态IP配置](https://www.cnblogs.com/maowenqiang/articles/7727910.html)
   - > [动态/静态IP配置](https://blog.csdn.net/n950814abc/article/details/79512834)
 
# 连接XShell
 1. 输入网络配置文件中的IP
 2. **用户身份验证**中填写要登录的账号


# 防火墙
   CentOS7 默认使用firewall防火墙，将其屏蔽，使用iptables。
   > [Linux系统中无iptables文件](https://blog.csdn.net/qq_18300109/article/details/79172019)
   > [centos7下没有iptables](https://www.cnblogs.com/flutehand/p/10304652.html)

# Mysql
## 登录
 1. linux切换到root
 2. mysql -uroot -p
 3. 输入密码

 > 执行 2命令 时，必须输入-uroot，否则执行命令会报错。（Ignoring query to other database）

## 卸载Mysql
 > [MySQL5.7 卸载 - Linux下卸载](https://blog.csdn.net/fanshujuntuan/article/details/78253877)

## 添加用户
 > [linux mysql添加用户名并实现远程访问](https://www.cnblogs.com/300js/p/7422878.html)