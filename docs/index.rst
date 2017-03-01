:orphan:

Flask-WXPay
=============

一个微信支付的Flask插件


Installation
------------
Install the module with one of the following commands::

    pip install Flask-WXPay

Usage
-----

initialized::

    from flask_wxpay import WXPay
    wxpay = WXPay()
    wxpay.init_app(app)

创建订单,生成prepay data::

    out_trade_no = wxpay.gen_out_trade_no()
    order_data = wxpay.unified_order(out_trade_no, price, ip, body, openid=openid)
    prepay_data = wxpay.get_jsapi_prepay_data(order_data['prepay_id'])


out_trade_no和out_refund_no生成规则
-----------------------------------

prefix + 一个随机小写字母(a-z) + datetime.now().strftime('%Y%m%d%H%M%S%f'),
例如: wxk20170214145251287492


配置项
------

==========================  =============================
WX_APPID                    公众账号ID
WXPAY_MCHID                 商户号
WXPAY_KEY                   商户支付密钥Key
WXPAY_NOTIFY_URL            默认异步通知url
WXPAY_CERT_PATH             默认值None
WXPAY_CERT_KEY_PATH         默认值None
WXPAY_OUT_TRADE_NO_PREFIX   out_trade_no前缀, 默认值wx。
WXPAY_OUT_REFUND_NO_PREFIX  out_refund_no前缀，默认值ref。
==========================  =============================



Reference
---------

.. toctree::
   :maxdepth: 2

   api
   exceptions