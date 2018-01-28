# weixincash
    微信现金红包
## Sample
**sample.php**
```php
require 'wxpay.class.php';//数组参数
$money = 100; //最低1元，单位分
$name = "测试";
$arr = array();
$arr['wxappid'] = ""; //appid
$arr['mch_id'] = "";//商户id
$arr['mch_billno'] = "商户ID".date('YmdHis').rand(1000,9999);//组合成28位，根据官方开发文档，可以自行设置
$arr['client_ip'] = $_SERVER['REMOTE_ADDR'];
$arr['re_openid'] = "************";//接收红包openid
$arr['total_amount'] = $money;
$arr['min_value'] = $money;
$arr['max_value'] = $money;
$arr['total_num'] = 100;
$arr['nick_name'] = $name;
$arr['send_name'] = $name;
$arr['wishing'] = "恭喜发财";
$arr['act_name'] = $name."红包";
$arr['remark'] = $name."红包";
 
$url = "https://api.mch.weixin.qq.com/mmpaymkttransfers/sendredpack";
$wxpay = new wxPay();
$res = $wxpay->pay($url, $arr);
var_dump($res);