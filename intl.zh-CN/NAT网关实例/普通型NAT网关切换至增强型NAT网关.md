# 普通型NAT网关切换至增强型NAT网关

增强型NAT网关兼容普通型NAT网关的全部功能，并在普通型NAT网关的技术架构上作了升级，具有更优的弹性和更强的稳定性，帮助您更好的管理公网访问流量。您可以将普通型NAT网关切换至增强型NAT网关。

2020年8月31日起至2020年9月30日止，您可以免费在NAT网关管理控制台自助将普通型NAT网关切换为增强型NAT网关。

**说明：** 目前，仅西南1（成都）、华北1（青岛）、英国（伦敦）、德国（法兰克福）、马来西亚（吉隆坡）和印度（孟买）地域支持将普通型NAT网关切换为增强型NAT网关，且需申请白名单。如需使用，请[提交工单](https://workorder-intl.console.aliyun.com/?spm=5176.11182172.nav-right.dticket.1e874882kUYyPy#/ticket/createIndex)。

将普通型NAT网关切换至增强型NAT网关前，您需要了解下图中的切换说明。

![了解事项](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6333659951/p147943.png)

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部菜单栏处，选择NAT网关的地域。

3.  在**NAT网关**页面，单击**立即切换**。

    ![立即切换](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6333659951/p146934.png)

4.  在**切换至增强型NAT网关**对话框，根据以下信息切换NAT网关。

    ![切换页面](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6333659951/p148992.png)

    |配置|说明|
    |--|--|
    |**选择NAT网关**|选择要切换至增强型NAT网关的普通型NAT网关。|
    |**为增强型NAT选择交换机**|选择增强型NAT网关的可用区和交换机。**说明：** 您需要为增强型NAT网关指定所属的交换机，指定成功后，系统会从该交换机内分配一个空闲IP来进行流量转发。请确保指定的交换机内有足够的空闲IP地址。 |

5.  单击**确定**。

6.  切换申请提交后，您可以单击**返回列表页**。

7.  在**NAT网关**页面，找到目标NAT网关实例，单击**状态**列下的**查看进度**查看切换进度。

    每个资源切换过程可能会持续5分钟，切换过程中会出现1~2次秒级闪断，业务重连即可恢复。

    ![查看进度](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6333659951/p147358.png)


