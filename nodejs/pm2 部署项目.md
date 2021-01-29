## pm2 部署项目



``` json
{
  "apps": [{
    //项目名称
    "name": "teaform",
    //启动文件
    "script": "index.js",
    //服务器部署路径
    "cwd": "/www/wwwroot/xiaobu-teaform-server",
    //运行模式
    "exec_mode": "fork",
    //超过最大内存自动重启
    "max_memory_restart": "1G",
    //程序运行小于60s异常退出
    "min_uptime": "60s",
    //异常退出重启次数
    "max_restarts": 30,
    //监听文件变化自动重启
    "watch": true,
    //排除监听的文件夹
    "ignore_watch": [
      "node_modules",
      "runtime",
      "static"
    ],
    //自动重启
    "autorestart": true,
    //传递给node的参数如 —harmony
    "node_args": [],
    //传递给脚本的参数
    "args": [],
    //环境变量
    "env": {
      "NODE_ENV": "production"
    }
  }]
}
```



### 执行php脚本

```json
{
  "name": "php-queue”,
  "args": "",
  "script": "./queue.php”,
  "exec_interpreter": "php",
  "exec_mode": "fork",
  "max_memory_restart": "100M"
}
```



### 启动 bash 脚本

`pm2 start script.sh`



### 参考:

https://www.jianshu.com/p/7b10123c8b88

https://www.jianshu.com/p/f1084c685e68

https://blog.csdn.net/chengxuyuanyonghu/article/details/74910875