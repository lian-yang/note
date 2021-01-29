### 源码安装



##### 切换到扩展源码目录

`cd ext/pcntl`

##### 执行phpize

`/Applications/MxSrvs/bin/php/bin/phpize`

##### 配置额外参数

`./configure --with-php-config=/Applications/MxSrvs/bin/php/bin/php-config`

##### 编译并安装

`make && make install`



### PECL 安装



##### 搜索扩展

`sudo pecl search pcntl`

##### 安装扩展

`sudo pecl install pcntl`



#### PS: 安装成功之后 修改php.ini 添加 extension=xxx.so 