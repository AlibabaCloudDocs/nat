为已分配固定公网IP的ECS实例统一公网出口IP 
=============================================

统一ECS实例的公网出口IP，有利于您更高效的管理互联网业务。本文为您介绍如何为已分配固定公网IP的ECS实例统一公网出口IP。

前提条件 
-------------------------

分配了固定公网IP的ECS实例所在的VPC已经配置了SNAT功能。更多信息，请参见[创建SNAT实现访问公网服务](/intl.zh-CN/基本功能操作/创建SNAT实现访问公网服务.md)。

背景信息 
-------------------------

NAT网关提供SNAT功能，为VPC内无公网IP的ECS实例提供访问互联网的代理服务。如果VPC内某些ECS实例已经分配了固定公网IP，这些ECS实例会优先通过固定公网IP访问互联网，而VPC内的其他ECS实例通过NAT网关的SNAT功能代理访问互联网，造成VPC内ECS实例的公网出口IP不一致，不利于统一管理业务。



![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2753651261/p49546.png)

您可以通过为ECS实例绑定弹性网卡来解决ECS实例公网出口IP不统一的问题。

如下图，您可以为ECS实例单独分配一块弹性网卡，并将固定公网IP转为EIP，然后将EIP绑定到弹性网卡，这样来自互联网的访问流量会经过弹性网卡到达ECS实例，当ECS实例需要访问互联网时会通过NAT网关进行转发。



![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2753651261/p49551.png)

步骤一：固定公网IP转EIP 
-----------------------------------

不同计费模式的ECS实例，对固定公网IP转EIP的支持不同： 



* 按量付费类型的ECS实例，支持直接将固定公网IP转为EIP。

  

* 包年包月类型的ECS实例，不支持直接将固定公网IP转为EIP。您需要先将包年包月ECS实例转为按量付费ECS实例，再将按量付费ECS实例的固定公网IP转为EIP。包年包月ECS实例转为按量付费ECS实例的详细操作说明，请参见[包年包月转按量付费](/intl.zh-CN/产品计费/转换计费方式/包年包月转按量付费.md)。

  




完成以下操作，将按量付费ECS实例的固定公网IP转为EIP。

1. 登录[云服务器ECS管理控制台](https://ecs.console.aliyun.com/#/home)。

   

2. 在左侧导航栏，选择 **实例与镜像** **\>** **实例** 。

   

3. 在顶部状态栏处，选择ECS实例的地域。

   

4. 在 **实例列表** 页面，找到目标ECS实例，选择 **操作** 列下的 **更多** **\>** **网络和安全组** **\>** **公网IP转换为弹性公网IP** 。![固定公网IP转换为EIP](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7222869161/p88779.png)

   

5. 在弹出的对话框中，单击 **确定** 。

   

6. 刷新实例列表。

   转换成功后，原来的公网IP地址会标注为 **弹性** 。![转换EIP成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7222869161/p88777.png)
   




步骤二：创建弹性网卡 
-------------------------------



1. 登录[云服务器ECS管理控制台](https://ecs.console.aliyun.com/#/home)。

   

2. 在左侧导航栏，选择 **网络与安全** **\>** **弹性网卡** 。

   

3. 选择弹性网卡的地域。 

   **说明**

   弹性网卡的地域必须与ECS实例的地域相同。
   

4. 在 **网卡列表** 页面，单击 **创建弹性网卡** 。

   

5. 在 **创建弹性网卡** 对话框，根据以下信息配置弹性网卡，然后单击 **确定** 。 

   * **网卡名称** ：输入弹性网卡的名称。

     
   
   * **专有网络** ：选择ECS实例所在的专有网络。

     
   
   * **交换机** ：选择ECS实例所在可用区的交换机。

     
   
   * **主私网IP** （可选）：输入弹性网卡的主私网IPv4地址。此IPv4地址必须属于交换机的CIDR网段中的空闲地址。如果您没有指定，创建弹性网卡时将自动为您分配一个空闲的私网IPv4地址。本文不指定主私网IP。

     
   
   * **辅助私网IP** （可选）：单击相应选项进行设置。本文选择不设置。

     
   
   * **安全组** ：选择当前专有网络的一个安全组。

     
   

   




更多参数信息，请参见[创建弹性网卡](/intl.zh-CN/网络/弹性网卡/创建弹性网卡.md)。

步骤三：将弹性网卡绑定到ECS实例 
--------------------------------------



1. 登录[云服务器ECS管理控制台](https://ecs.console.aliyun.com/#/home)。

   

2. 在左侧导航栏中，选择 **网络与安全** **\>** **弹性网卡** 。

   

3. 选择弹性网卡的地域。

   

4. 在 **网卡列表** 页面，找到目标弹性网卡，单击 **操作** 列下的 **绑定实例** 。

   

5. 在弹出的对话框中，选择要绑定的ECS实例，然后单击 **确定** 。

   




步骤四：将EIP与ECS实例解绑 
-------------------------------------



1. 登录[专有网路管理控制台](https://vpcnext.console.aliyun.com)。

   

2. 在左侧导航栏，单击 **弹性公网IP** 。

   

3. 选择EIP的地域。

   

4. 在 **弹性公网IP** 页面，找到目标EIP，单击 **操作** 列下的 **解绑绑定** 。

   

5. 在弹出的对话框中，单击 **确定** 。

   




步骤五：将EIP绑定到弹性网卡 
------------------------------------



1. 登录[专有网络管理控制台](https://vpcnext.console.aliyun.com)。

   

2. 在左侧导航栏，单击 **弹性公网IP** 。

   

3. 选择EIP的地域。

   

4. 在 **弹性公网IP** 页面，找到目标EIP，单击 **操作** 列下的 **绑定资源** 。

   

5. 在 **绑定弹性公网IP至资源** 对话框，根据以下信息绑定EIP至弹性网卡，然后单击 **确定** 。 

   * **实例类型** ：选择辅助弹性网卡。

     
   
   * **资源组** （可选）：选择该EIP所属的资源组。本文选择默认资源组。

     
   
   * **绑定模式** （可选）：选择EIP绑定模式。 本文选择 **普通模式** 。

     
   
   * **选择要绑定的** ：选择要绑定的辅助弹性网卡。

     
   

   




步骤六：配置网卡路由 
-------------------------------

1. 登录[ECS管理控制台](https://ecs.console.aliyun.com)。

   

2. 在左侧导航栏，选择 **网络与安全** **\>** **弹性网卡** 。

   

3. 查看ECS实例的弹性网卡信息如下图所示。![网卡](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3661434261/p285986.png)

   

4. 远程登录ECS实例，更多信息，请参见[ECS实例连接方式概述](t9618.html#concept-tmr-pgx-wdb)。

   

5. 执行`ip a`命令查看弹性网卡信息。![网卡信息](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3661434261/p285988.png)

   经过查看，得到ECS实例弹性网卡的信息如下：

   eth0：主网卡，私网地址：192.168.3.10

   eth1：辅助弹性网卡，私网地址：192.168.3.11 公网地址：118.190.XX.XX
   

6. 按您的需要规划路由表里每块网卡的默认路由 **metric** 值。 

   执行以下命令，查看 **Gateway** 和 **metric** 值。

   `route -n`

   查询结果如下所示：![metric](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7465064261/p285993.png)
   **说明**

   本文以一块辅助弹性网卡为例，查看到辅助弹性网卡的 **metric** 值大于主网卡的 **metric** 值，路由优先级低于主网卡，不需要执行重新规划网卡的 **metric** 值，保持默认配置即可。如有多块辅助弹性网卡，请根据实际情况配置，具体操作，请参见[配置网卡路由](/intl.zh-CN/网络/弹性网卡/配置弹性网卡.md)。

   

7. 创建路由表。

   1. 执行以下命令创建路由表。

      `ip -4 routeadd default via 192.168.3.13 dev eth1 table 101`
      **说明**

      建议路由表名称和网卡的默认路由 **metric** 取值保持一致，如本例中的101。
      
   
   2. 执行以下命令检查路由表是否创建成功。

      `ip routelist table 101`

      查询结果如下所示：

      ![路由](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7465064261/p286028.png)
      
   

   

8. 配置策略路由。

   1. 执行以下命令创建策略路由。

      `ip -4 ruleadd from 192.168.3.71 lookup 101`
      
   
   2. 执行以下命令查看路由规则。

      `ip rule list`

      查询结果如下所示：![策略路由](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7465064261/p286031.png)
      
   

   




步骤七：测试网络连通性 
--------------------------------

完成以下操作，测试互联网是否可以通过弹性网卡绑定的EIP访问ECS实例。本操作以本地Linux设备远程连接ECS实例为例。 


**说明**

远程连接ECS实例，请确认ECS实例的安全组已放行SSH（22）端口。更多信息，请参见[添加安全组规则](/intl.zh-CN/安全/安全组/添加安全组规则.md)。

1. 登录本地Linux设备。

   

2. 执行`ssh root@公网IP`命令，然后输入ECS实例的登录密码，查看是否可以远程连接到实例。 

   若界面上出现`Welcome to Alibaba Cl``oud Elastic Compute Service!`时，表示您已经成功连接到实例。![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8465064261/p286037.png)
   




完成以下操作，测试ECS实例是否可以通过NAT网关的SNAT功能主动访问互联网。本操作以在ECS实例上查看公网出口IP为例。 



1. 登录ECS实例。

   

2. 执行`curl https://myip.ipip.net`查看公网出口IP。 

   若公网出口IP与NAT网关SNAT条目中的IP一致，即ECS实例优先通过NAT网关的SNAT功能主动访问互联网。![验证2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3986434261/p286038.png)
   




