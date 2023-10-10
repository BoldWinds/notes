# JWT

https://jwt.io/introduction

## 简介

JWT是一个使用Json形式在多方安全传输信息的标准，他可以采用对称加密的HMAC算法，或者非对称加密的RSA或ECDSA算法

JWT主要有以下两个用途：

- 认证：只要用户登陆，他后续所有的请求都会带有jwt用于身份认证
- 信息交换

## 结构

JWT由三个部分组成，每个部分用`.`分隔：

- Header
- Payload
- Signature

### Header

一般由两个部分组成：

```json
{
  "alg": "HS256",     // 算法
  "typ": "JWT"
}
```

### Payload

Payload由claims组成，claim是实体(如用户)的状态和附加的数据。claim有以下三种：

- Registered Claim
- Public Claim
- Private Claim

例如：

```json
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}

```

### Signature







## 运行

![image-20230915152641860](https://lbw-img-lbw.oss-cn-beijing.aliyuncs.com/img/202309151526978.png)





















