基于Upush的服务端官方示例文件修改
-
- 增加命名空间
- 推送到packagist

安装：
```bash
composer require thanatos915/umeng
```

单播

```php
use Umeng\UmengPush;

$key = "****";
$secret = "*****";
$push = new UmengPush($key, $secret);
$values = [
    'ticker' => '1', // require 通知栏提示文字
    'title' => '2', // require 通知标题
    'text' => '3', // require 通知文字描述
    'after_open' => 'go_app' // require 值可以为:
    // "go_app": open app
    // "go_url": 跳转到URL
    // "go_activity": open activity
    // "go_custom": 用户自定义内容。
];
echo $push->sendAndroidUnicast($values, [], 'device token');
# result: {"ret":"SUCCESS","data":{"msg_id":"uu77312149835056871500"}}
```
广播
```php
$key = "****";
$secret = "*****";
$push = new UmengPush($key, $secret);
$values = [
    'ticker' => '1', // 必填 通知栏提示文字
    'title' => '2', // 必填 通知标题
    'text' => '3', // 必填 通知文字描述
    'after_open' => 'go_app' // 必填 值可以为:
    // "go_app": 打开应用
    // "go_url": 跳转到URL
    // "go_activity": 打开特定的activity
    // "go_custom": 用户自定义内容。
];
echo $push->sendAndroidBroadcast($values, []);
# result: {"ret":"SUCCESS","data":{"task_id":"us41183149835484509400"}}
```
