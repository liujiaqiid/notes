# JSON Web Token JWT

## JWT

- JWT 属于IETF的RFC-7519开放标准,旨在安全传输JSON对象,定义了压缩和信息自足方式,可用于认证和信息交换;
- JWT压缩后的信息可以存放在URL、Header或者Post参数中;
- 支持加密方式包括：HMAC-SHA256(对称加密);RSA(public/private key 非对称加密); RSA加解密速度比HMAC慢;
- JWT包括三部分：Header、Payload、Signature;
- 可用于无状态的认证，每次访问携带JWT，进行认证授权; JWT的信息自足，可以避免多次查询数据库;
- Use case:  
```
How we use JSON Web Tokens in Auth0?
In Auth0, we issue JWTs as a result of the authentication process.
When the user logs in using Auth0, a JWT is created, signed, and sent to the user.
Auth0 supports signing JWT with both HMAC and RSA algorithms.
This token will be then used to authenticate and authorize with APIs which will grant access to their protected routes and resources.
We also use JWTs to perform authentication and authorization in Auth0’s API v2, replacing the traditional usage of regular opaque API keys.
Regarding authorization, JSON Web Tokens allow granular security, that is the ability to specify a particular set of permissions in the token, which improves debuggability.
```

## Refs:
- [JWT](https://jwt.io/introduction/)
- [JWT_auth0](https://auth0.com/learn/json-web-tokens/)
