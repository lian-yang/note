## Composer 包管理工具使用



全局安装

`curl -sS https://getcomposer.org/installer | php`

`mv composer.phar /usr/local/bin/composer`



切换全局源

`composer config -g repo.packagist composer https://packagist.phpcomposer.com`



composer自身版本升级到最新

`composer self-update`



安装依赖到 vendor 目录下

`composer install`



更新全部依赖包 -vvv 输出过程

`composer update`

更新指定包依赖包

`composer update vendor/package vendor/package2`



添加依赖包

`composer requrie vendor/package`

添加开发依赖包

`composer requrie vendor/package —dev`

指定依赖包版本

`composer requrie vendor/package:^1.0`



删除依赖

`composer remove vendor/package`



执行诊断命令

`composer diagnose`



清除缓存

`composer clear`



若项目之前已通过其他源安装，则需要更新 composer.lock 文件

`composer update --lock`



版本约束

\* 不限定版本

dev-master 前缀加分支名、一般在开发环境使用

**~** 约束符锁定小版本的方式 ~1.2 表示 >= 1.2 并且 < 2.0 的版本 

**^** 约束符锁定大版本 ^1.2 表示任意大于等于 1.2 的 1.x.x 版本 < 2.0 的版本



自动加载

`require 'vendor/autoload.php';`

```json
{

    "autoload": {

        "psr-4": {

            "app\\": "application"

        },

        "classmap": [

            "library/“,

            “util/“,

        ],

        "files" : [

            "function.php",

            "common.php"

        ]

    }

}
```



打印自动加载索引、更新autoloader

`composer dump-autoload`



参考文档

https://docs.phpcomposer.com/



其他源

腾讯云 https://mirrors.cloud.tencent.com/composer/

阿里云 https://mirrors.aliyun.com/composer/