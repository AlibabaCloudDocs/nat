# Service-linked roles for NAT Gateway

This topic describes the service-linked role AliyunServiceRoleForNatgw for NAT Gateway and how to delete the service-linked role.

## What is a service-linked role?

A service-linked role is a Resource Access Management \(RAM\) role that can be assumed only by the linked service. An Alibaba Cloud service may need to access other services to use a specific feature. Before you can access a service, make sure that you are authorized to access the service. Service-linked roles simplify the authorization process and avoid risks caused by user errors. For more information, see [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md).

## Create a service-linked role

When you create an enhanced NAT gateway that does not have a service-linked role, the system automatically creates the service-linked role AliyunServiceRoleForNatgw for the NAT gateway. Then, the system adds the permission policy AliyunServiceRolePolicyForNatgw to the role. This allows the NAT gateway to access other resources on Alibaba Cloud. The following content shows the content of the permission policy:

**Note:** When you create a standard NAT gateway, the system does not automatically create the service-linked role AliyunServiceRoleForNatgw for the NAT gateway.

```
{
    "Version": "1",
    "Statement": [
        {
            "Action": [
                "vpc:DescribeVSwitchAttributes"
            ],
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": [
                "ecs:CreateNetworkInterface",
                "ecs:CreateSecurityGroup",
                "ecs:AuthorizeSecurityGroup",
                "ecs:RevokeSecurityGroup",
                "ecs:DeleteSecurityGroup",
                "ecs:JoinSecurityGroup",
                "ecs:DeleteSecurityGroup",
                "ecs:LeaveSecurityGroup",
                "ecs:DescribeSecurityGroups",
                "ecs:AttachNetworkInterface",
                "ecs:DetachNetworkInterface",
                "ecs:DeleteNetworkInterface",
                "ecs:DescribeNetworkInterfaces",
                "ecs:CreateNetworkInterfacePermission",
                "ecs:DescribeNetworkInterfacePermissions",
                "ecs:DeleteNetworkInterfacePermission",
                "ecs:CreateSecurityGroupPermission",
                "ecs:AuthorizeSecurityGroupPermission",
                "ecs:RevokeSecurityGroupPermission",
                "ecs:DeleteSecurityGroupPermission",
                "ecs:JoinSecurityGroupPermission",
                "ecs:DeleteSecurityGroupPermission",
                "ecs:LeaveSecurityGroupPermission",
                "ecs:DescribeSecurityGroupPermissions",
                "ecs:AttachNetworkInterfacePermissions",
                "ecs:DetachNetworkInterfacePermissions"
            ],
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": "ram:DeleteServiceLinkedRole",
            "Resource": "*",
            "Effect": "Allow",
            "Condition": {
                "StringEquals": {
                    "ram:ServiceName": "nat.aliyuncs.com"
                }
            }
        }
    ]
}
```

## Delete the service-linked role

If you want to delete the service-linked role AliyunServiceRoleForNatgw for NAT Gateway, you must first delete the NAT gateway that is linked with the role. For more information, see the following topics:

-   [Delete a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.md)
-   [Delete a service-linked role](/intl.en-US/RAM Role Management/Service-linked roles.md)

