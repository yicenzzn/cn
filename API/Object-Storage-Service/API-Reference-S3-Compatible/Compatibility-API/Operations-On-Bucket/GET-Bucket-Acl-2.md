# Get Bucket Acl

## 描述
该操作可列出指定Bucket，仅Bukcet的Owner可操作。

## 请求
### 语法
```HTTP
GET /?acl HTTP/1.1
Host: <BUCKET_NAME>.s3.<REGION>.jdcloud-oss.com
Date: <date>
Authorization: <authorization string> (see Authenticating Requests (AWS Signature Version4))
```

###  请求参数
无请求参数
### 请求Header
无特殊请求Header
### 请求元素
无请求元素

## 响应
### 响应Header
无特殊响应Header
### 响应元素

名称|描述
---|---
AccessControlList|acl信息集合<br>Type: Container<br>Ancestors: AccessControlPolicy
AccessControlPolicy|每个被授予人的ACL元素集合。<br>Type: String<br>Ancestors: None
DisplayName|Bucket拥有者名称。<br>Type: String<br>Ancestors: AccessControlPolicy.Owner
Grant|被授权者及权限信息集合<br>Type: Container<br>Ancestors: AccessControlPolicy.AccessControlList
Grantee|被授权者<br>Type: String<br>Ancestors: AccessControlPolicy.AccessControlList.Grant
ID|bucket拥有者或者被授权者的ID<br>Type: String<br>Ancestors: AccessControlPolicy.Owner<br> AccessControlPolicy.AccessControlList.Grant
Owner|bucket拥有者的信息集合<br>Type: Container<br>Ancestors: AccessControlPolicy
Permission|指定的权限<br>Type: String<br>Valid Values: FULL_CONTROL、WRITE、READ <br>Ancestors: AccessControlPolicy.AccessControlList.Grant

## 示例
### 请求示例
```HTTP
GET ?acl HTTP/1.1
Host: <BUCKET_NAME>.s3.<REGION>.jdcloud-oss.com
Date: Wed, 28 Oct 2009 22:32:00 GMT
Authorization: <authorization string>
```
### 响应示例
```HTTP
HTTP/1.1 200 OK
x-amz-request-id: 318BC8BC148832E5
Date: Wed, 28 Oct 2009 22:32:00 GMT
Last-Modified: Sun, 1 Jan 2006 12:00:00 GMT
Content-Length: 124
Content-Type: text/plain
Connection: close
Server: JDCloudOSS

<AccessControlPolicy>
  <Owner>
    <ID>75aa57f09aa0c8caeab4f8c24e99d10f8e7faeebf76c078efc7c6caea54ba06a</ID>
    <DisplayName>CustomersName@amazon.com</DisplayName>
  </Owner>
  <AccessControlList>
    <Grant>
      <Grantee xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
			xsi:type="CanonicalUser">
        <ID>75aa57f09aa0c8caeab4f8c24e99d10f8e7faeebf76c078efc7c6caea54ba06a</ID>
        <DisplayName>CustomersName@amazon.com</DisplayName>
      </Grantee>
      <Permission>FULL_CONTROL</Permission>
    </Grant>
  </AccessControlList>
</AccessControlPolicy> 
```
