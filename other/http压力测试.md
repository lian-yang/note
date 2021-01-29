## 🔧 HTTP压力测试



### Wrk压力测试

参数：-t 线程数 -c tcp连接数 -d 压测时间

`wrk -t10 -c1000 -d30s https://baidu.com`



### Ab压力测试

参数：-n 请求数 -c 并发数 -T 设置content-type -C 添加cookie -H 添加请求头

`ab -n 10 -c 2 https://baidu.com`