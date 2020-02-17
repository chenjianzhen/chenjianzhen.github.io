title: python&twilio发送短信
date: 2020-02-17 19:53:57

tags:

-python

# python发送短信

短信的应用场景很广泛，手机APP的验证啊登录；监控服务器；密码修改验证；10086催你还话费等等。



在知乎上看到的：[https://zhuanlan.zhihu.com/p/100664465](https://zhuanlan.zhihu.com/p/100664465)

需要使用的网站：[http://www.twilio.com](http://www.twilio.com)

据说这个网站发免费短信支持条数是最多的，抱着好玩的心态就来试一试。



#### 准备工作

进入网站：
{% asset_img 1.png 1.png %}


1. 注册账户

2. 验证邮箱

3. 验证手机

4. 填写选项

5. 获取服务端提供的号码

   功能：

   - 可以给认证过的手机号发送短信或来电
   - 短信和来电会包含“Twilio trial account”的注释

   {% asset_img 2.png 2.png %}

   {% asset_img 3.png 3.png %}

   {% asset_img 4.png 4.png %}

   {% asset_img 5.png 5.png %}



### 代码演示

#### 发送短信

右上角"Helper" --> "helper library"

{% asset_img 6.png 6.png %}

接下来就参照官方文档进行操作了。

安装twilio库，该库可以帮助我们从python应用程序与Twilio API进行交互。

~~~
pip install twilio
~~~

安装过程会有一些依赖项需要安装，等它自己安装完。



复制官方demo，进行修改

~~~python
from twilio.rest import Client

# 你个人的账户SID，在你的控制台(console)主页上
account_sid = "xxx"
# 你的验证令牌,位于在账户SID下面
auth_token  = "xxx"

client = Client(account_sid, auth_token)

message = client.messages.create(
    to="+86xxx",        # 在验证手机号时你留下的号码，记得加上"+86"
    from_="+xxx",       # 获取的实验号码(Trial Number)，在控制台主页上
    body="A message send by python&twilio!")

print(message.sid)
~~~



收到的短信：

{% asset_img 7.png 7.png %}

发送完一条短信后，剩余金额：

{% asset_img 8.png 8.png %}

也就是一条短信花费$0.03，折合RMB：￥0.21。

一共可以发送$14.50/$0.03 = 483条短信(四舍五入后)。

账单更精确一些。。。

{% asset_img 9.png 9.png %}