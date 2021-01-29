## Nginx 学习笔记



### 负载均衡

``` nginx
upstream backserver {
    ip_hash;
    server ip:port;
    server ip:port;
}
```



### 反向代理

``` nginx
location ~* /(api|graphql) {
    # 将客户端的 Host 和 IP 等信息一并转发到对应节点
    proxy_redirect off;
    proxy_set_header   X-Forwarded-Proto $scheme;
    proxy_set_header   Host              $http_host;
    proxy_set_header   X-Real-IP         $remote_addr;
    proxy_set_header   X-Forwarded-For   $proxy_add_x_forwarded_for;

    # WebSocket 代理 Header
    proxy_http_version 1.1;
    proxy_set_header Upgrade websocket;
    proxy_set_header Connection "Upgrade";

    # 执行代理访问真实服务器
    proxy_pass http://backserver;
}
```