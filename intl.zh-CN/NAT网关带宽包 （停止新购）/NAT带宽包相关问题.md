# NAT带宽包相关问题

-   [为什么NAT网关控制台不能购买NAT带宽包？](#section_bfi_b1c_dzq)
-   [一个NAT网关支持绑定多少个NAT带宽包？](#section_zye_aty_rlc)
-   [NAT带宽包与共享带宽有什么区别？](#section_r8u_xbe_6og)
-   [NAT带宽包中的公网IP与EIP有什么区别？](#section_ht8_tnb_0nf)
-   [NAT带宽包支持创建SNAT IP地址池吗？](#section_0z3_fez_245)
-   [NAT带宽包的带宽峰值是否同时针对出方向和入方向？](#section_w6i_gu2_747)

## 为什么NAT网关控制台不能购买NAT带宽包？

对于2017年11月3日23：59分2018年1月26日23：59分之前账号下没有NAT带宽包的全部用户，使用流程升级为EIP绑定NAT网关的形式。EIP绑定NAT网关的操作说明，请参见[绑定EIP]()。

## 一个NAT网关支持绑定多少个NAT带宽包？

默认支持绑定4个NAT带宽包。

您可以在配额管理页面，找到配额名称natgw\_quota\_bandwidth\_packages\_num，然后申请调整。

## NAT带宽包与共享带宽有什么区别？

NAT带宽包只能绑定NAT网关，使用范围较窄。

共享带宽可以在云服务器ECS和负载均衡（SLB）等场景中使用，使用范围更宽泛。

## NAT带宽包中的公网IP与EIP有什么区别？

NAT带宽包中的公网IP不可以解绑。

EIP可以随时解绑和绑定。

## NAT带宽包支持创建SNAT IP地址池吗？

支持，目前只支持通过API创建SNAT IP地址池。详细信息，请参见[创建SNAT IP地址池](https://yq.aliyun.com/articles/533821)。

## NAT带宽包的带宽峰值是否同时针对出方向和入方向？

NAT带宽包的带宽峰值针对的是出方向流量，但入方向流量也会根据带宽峰值做相应的限速。

