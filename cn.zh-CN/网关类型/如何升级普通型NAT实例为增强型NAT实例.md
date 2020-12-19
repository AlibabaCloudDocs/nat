---
keyword: [NAT网关, 增强型, 网络地址转换, 提供公网服务, 访问公网]
---

# 如何升级普通型NAT实例为增强型NAT实例

增强型NAT网关在普通型NAT网关的技术架构上做了升级，具有更优的弹性和更强的稳定性，帮助您更好的管理公网访问流量。2020年10月1日起至2020年12月31日止，您可以免费在NAT网关控制台自助将普通型NAT网关升级至增强型NAT网关。

## 升级说明

将普通型NAT网关升级至增强型NAT网关前，您需要了解下图中的升级说明。

![了解事项](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6333659951/p147943.png)

## 升级至增强型NAT网关

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部菜单栏，选择NAT网关的地域。

3.  在**NAT网关**页面，单击**立即升级**。

    如果您不是首次升级，请单击**继续升级**。

    ![立即切换](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7856431061/p146934.png)

4.  在**升级至增强型NAT网关**对话框，选中**我已知晓上述内容，确认进行升级**，完成以下配置以升级NAT网关的网关类型，然后单击**确定**。

    ![切换页面](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9273057061/p148992.png)

    |配置|说明|
    |--|--|
    |**选择NAT网关**|选择要升级的普通型NAT网关。|
    |**为增强型NAT选择交换机**|选择增强型NAT网关的可用区和交换机。**说明：** 您需要为增强型NAT网关指定所属的交换机，指定成功后，系统会从该交换机内分配一个空闲IP来进行流量转发。请确保指定的交换机内有足够的空闲IP地址。 |

5.  升级申请提交后，您可以单击**返回列表页**。

6.  在**NAT网关**页面，找到目标NAT网关实例，单击**状态**列下的**查看进度**查看升级进度。

    每个资源升级过程可能会持续5分钟，升级过程中会出现1~2次秒级闪断，业务重连即可恢复。

    ![查看进度](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4677431061/p147358.png)


**相关文档**  


[增强型NAT网关（新推出）](/cn.zh-CN/网关类型/增强型NAT网关（新推出）.md)

[t2005535.md\#]()

