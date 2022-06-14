

# 1.3 添加转发规则（杭州BGP高防）
##  添加域名转发规则
购买高防-\>选择“华东BGP 杭州”线路高防-\>购买成功-\>详情-\>IP管理-\>管理。
配置[域名转发策略、CC防护规则](https://docs.ucloud.cn/uewaf/features/rule/UWAF_rule).
##  添加IP或TCP转发规则 

购买高防-\>选择对应线路高防-\>购买成功-\>详情-\>IP管理-\>添加IP-\>确定-\>高防IP添加成功。

![](/images/uads/opintro/杭州添加IP.png)

点击规则管理----添加规则，可以配置高防IP的转发规则。

![](/images/uads/opintro/添加转发规则.png)

**负载模式:**

  - 不负载：高防IP+端口对应源站IP+端口进行转发。最多可配置50条转发策略。
  - 负载：将访问到高防IP+端口的流量在源站池中进行轮询负载。一个IP可配置2条负载策略，每个策略最多可以配置31个源站。

**源站IP端口：** 真实业务服务器的IP和端口，支持非UCloud平台的主机。建议使用一个未曾使用过的源站IP接入高防，避免之前的源站IP暴露导致黑客绕过高防直接攻击源站。

高级设置:如果不勾选只能配置高防IP和源站IP一对一的IP转发。勾选后可以配置高防IP和源站IP直接的TCP/UDP端口转发。

协议类型:

  - IP：高防IP和源站IP进行一对一的IP转发。
  - TCP：高防IP和源站IP进行TCP端口转发。

高防IP端口:需要对外提供服务的高防IP和端口。如有有多个高防IP可通过下拉框选择。

获取用户真实IP：关闭后源站上看到的客户端源地址为高防回源地址。开启后高防转发设备会将用户的真实IP地址封装到TCP
option中，源站可通过安装TOA模块获取。

TOAID:源站TOA模块将根据此ID通过TCP option获取用户真实IP。UCloud提供的TOA模块默认值是200。

``` 
 TOA模块安装方式参考：https://docs.ucloud.cn/uantiddos/uads/faq/howtogetip
```

配置完后续的转发规则后。将业务切到高防IP或者将域名通过cname的方式解析的高防域名即可完成业务切换。