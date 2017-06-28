* 介绍
阿里大于关闭了新用户渠道，迁移到阿里云短信服务上，然而阿里云短信服务在5月底更新了api。
在github上找了一下，轮子都是基于2016年的接口，非常难受。
自己造了一个轮子，亲测可用。

* 安装
` composer require mrgoon/aliyun-sms dev-master `

* 加载
在config/app的providers中添加
` Mrgoon\AliSms\ServiceProvider::class `
同时，可以选择性添加aliases
控制台运行:
` php artisan vendor:publish `
根据新增的` aliyunsms.php ` 文件添加部分环境变量：
``` 
ALIYUN_SMS_ENABLE_HTTP_PROXY=false
ALIYUN_SMS_HTTP_PROXY_IP=127.0.0.1
ALIYUN_SMS_HTTP_PROXY_PORT=8888
ALIYUN_SMS_REGION_ID=cn-hangzhou
ALIYUN_SMS_AK=your access key
ALIYUN_SMS_AS=your secret key
ALIYUN_SMS_SIGN_NAME=sign name
```

* 使用
```
$aliSms = new AliSms();
$response = $aliSms->sendSms('phone number', 'SMS_code', ['name'=> 'value in your template']);
//dump($response);
```