## adb常用操作



### \#查看所有连接设备

`adb devices`

### \#连接指定设备或模拟器

`adb -s emulator-5554`

### \#获取设备已安装的第3方app包

`adb -s emulator-5554 shell pm list packages -3`

### \#查看前台 Activity

`adb -s emulator-5554 shell dumpsys activity activities | grep mResumedActivity`

### \#查看正在运行的 Services

`adb -s emulator-5554 shell dumpsys activity services com.xunmeng.pinduoduo`

### \#启动拼多多商品详情页

`adb -s emulator-5554 shell am start -d "pinduoduo://com.xunmeng.pinduoduo/goods.html?goods_id=74058586702"`