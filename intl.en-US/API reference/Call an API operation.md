# Call an API operation

The NAT Gateway and Virtual Private Cloud \(VPC\) APIs share the same endpoint. To call the NAT Gateway API, you must send HTTP GET requests to the endpoint of the NAT Gateway API. You must add the request parameters that correspond to the API operation being called. After you call the API operation, the system returns a response. The request and response are both encoded in UTF-8.

## Request syntax

NAT Gateway API operations use the remote procedure call \(RPC\) protocol. You can call NAT Gateway API operations by sending HTTP GET requests.

Use the following request syntax:

```
http://Endpoint/?Action=xx&Parameters
```

where:

-   Endpoint: the endpoint of the NAT Gateway API is `vpc.aliyuncs.com`.
-   Action: the name of the operation being performed. For example, to create a NAT gateway, you must set the Action parameter to CreateNatGateway.
-   Version: the version of the API that you want to use. The current NAT Gateway API version is 2016-04-28.
-   Parameters: the request parameters for the operation. Separate multiple parameters with ampersands \(&\).

    Request parameters include both common parameters and operation-specific parameters. Common parameters include information such as the API version number and authentication information. For more information, see [Common parameters](/intl.en-US/API reference/HTTP Requests/Common parameters.md).


The following example demonstrates how to call the CreateNatGateway operation to create a NAT gateway:

**Note:** The following code has been edited to improve readability.

```
https://vpc.aliyuncs.com/?Action=CreateNatGateway
&Format=xml
&Version=2016-04-28
&Signature=xxxx%xxxx%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&Timestamp=2012-06-01T12:00:00Z
…
```

## Authorization

To ensure the security of your account, we recommend that you call NAT Gateway API operations as a Resource Access Management \(RAM\) user. To call NAT Gateway API operations as a RAM user, you must create and attach permission policies to the RAM user.

For more information about the NAT Gateway resources and API operations that can be authorized to RAM users, see [RAM authentication](/intl.en-US/API reference/RAM authentication.md).

## Signature

You must sign all API requests to ensure security. Alibaba Cloud uses the request signature to verify the identity of the API caller.

NAT Gateway implements symmetric encryption with an AccessKey pair to verify the identity of the request sender. An AccessKey pair is an identity credential issued to Alibaba Cloud accounts and RAM users that is similar to a pair of username and password. An AccessKey pair consists of an AccessKey ID and an AccessKey secret. The AccessKey ID is used to verify the identity of the user, while the AccessKey secret is used to encrypt and verify the signature string. You must keep your AccessKey secret confidential.

You must add the signature to the NAT Gateway API request in the following format:

`https://endpoint/?SignatureVersion=1.0&SignatureMethod=HMAC-SHA1&Signature=XXXX%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx`

CreateNatGateway is used as an example. Assume that the AccessKey ID is `testid` and the AccessKey secret is `testsecret`. The following sample code shows the URL of the request before the request is signed:

```
http://vpc.aliyuncs.com/?Action=CreateNatGateway
&Timestamp=2016-05-23T12:46:24Z
&Format=XML
&AccessKeyId=testid
&SignatureMethod=HMAC-SHA1
&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx
&Version=2014-05-26
&SignatureVersion=1.0
```

Perform the following operations to calculate the signature:

1.  Create a string-to-sign by using the request parameters:

    ```
    GET&%2F&AccessKeyId%3Dtestid&Action%3DCreateNatGateway&Format%3DXML&SignatureMethod%3DHMAC-SHA1&SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx&SignatureVersion%3D1.0&TimeStamp%3D2016-02-23T12%253A46%253A24Z&Version%3D2014-05-15
    ```

    .

2.  Calculate the HMAC value of the string-to-sign.

    Append an ampersand \(&\) to the AccessKey secret as the key to calculate the HMAC value. In this example, the key is `testsecret&`.

    ```
    CT9X0VtwR86fNWS********juE=
    ```

3.  Add the signature string to the request as the Signature parameter.

    ```
    http://vpc.aliyuncs.com/?Action=CreateNatGateway
    &Timestamp=2016-05-23T12:46:24Z
    &Format=XML
    &AccessKeyId=testid
    &SignatureMethod=HMAC-SHA1
    &SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx
    &Version=2014-05-26
    &SignatureVersion=1.0
    &Signature=XXXX%3D
    ```


