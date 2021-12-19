# 一键脚本配置V2ray+WS+TLS+Web科学上网梯子详细教程

## V2ray+tls+ws介绍
简要地说就是可以把你的科学上网行为变成正常的访问https网页，使得GFW很难得知你看起来是在正常上网其实是在科学上网，由于https使用TLS加密，所以与服务端的内容理论上是不可被解密的，既保证了数据安全又保证了行为安全。好吧说的可能不清晰，可以参考之前写的一篇文章,也可以参考v2ray的通俗版教程。

## 购买VPS
虽然是一键脚本，但是使用脚本的前提还是你有个vps，和一个解析到vps的域名，首先来讲一下购买vps，现在可以购买vps的云平台很多，之前用的digitalocean,最主要的原因是因为可以随时删除重建服务器，等于可以随时更换被墙的ip。后来用Vultr了，因为发现除了和DO一样可以随时换ip，重点是还有日本的节点，而且支持支付宝，大陆使用日本的节点可以说速度飞快了。

## 优惠购买云服务器vultr

在搭建之前需要一台境外的云服务器，而 [vultr](https://www.vultr.com/?ref=8944093-8H) 服务商比较稳定，安全，相当于境内的阿里云。

值得说的一点是， [vultr](https://www.vultr.com/?ref=8944093-8H) 给新用户的福利相当给力，充值 10 美元就可以获取 100 美元，你可以点击 [vultr 专属赠送新用户 100 美元](https://www.vultr.com/?ref=8944093-8H) 进去抢先注册。

右上角有注册按钮，你也可以切换成中文界面：

<img width="1446" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119019442-be0cc500-b98c-11eb-895b-0d6300dce93d.png">

![](https://user-images.githubusercontent.com/84239400/119019760-0d52f580-b98d-11eb-9837-aba0990f1dfb.png)

接着使用邮箱和密码就可以注册了。

![](https://user-images.githubusercontent.com/84239400/119020042-4ee3a080-b98d-11eb-8341-bfc30f4b103c.png)

进去之后你可以看到这个页面，说明你已经通过 [vultr 专属优惠链接](https://www.vultr.com/?ref=8872890-6G) 获得了 100 美元赠送的资格：

![](https://user-images.githubusercontent.com/84239400/119020173-733f7d00-b98d-11eb-8ecc-a1afeb556fe6.png)

现在你只要选择支付宝充值 10 美元以上，就可以获得额外赠送的 100 美元。

![](https://user-images.githubusercontent.com/84239400/119020280-966a2c80-b98d-11eb-9113-8f5f0b75c5ea.png)

接下来就可以在这个平台选购云服务器了。

点击页面左边菜单栏的 「Products」进入服务器选购页面。

### Choose Server 选择服务器

选择 Cloud Compute 即可：

![](https://user-images.githubusercontent.com/84239400/119020373-af72dd80-b98d-11eb-8478-02d735b82709.png)

### Server Location

服务器的位置，可以选择美国地区，比如纽约：

![](https://user-images.githubusercontent.com/84239400/119020467-cadde880-b98d-11eb-8927-d3d837bbc20c.png)

### Server Type

服务器类型，CentOS 8 x64 系统：

<img width="1297" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119020720-198b8280-b98e-11eb-9df3-19bf5a187a1e.png">

### Server Size

内存，个人使用10G完全够用，这里选择3.5美元一个月，性价比高，注意不要选择IPv6 ONLY的，要不然无法搭建使用。

<img width="1240" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119020895-4a6bb780-b98e-11eb-9ac8-3cdd4f4397de.png">

选择完了之后，下面的其它东西都不需要填，直接点击右下角 Deploy Now 就可以了：

![](https://user-images.githubusercontent.com/84239400/119020981-68391c80-b98e-11eb-9f16-00c75de88eeb.png)

这时候你就拥有了自己的一台云服务器了：

<img width="1261" alt="VPN搭建教程" src="https://user-images.githubusercontent.com/84239400/119021075-86068180-b98e-11eb-82a9-71edb9934f23.png">


点击 Cloud Instance ，可以看到你服务器的 IP 地址和密码：

<img width="1308" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119021183-a20a2300-b98e-11eb-8ff4-7f18d3e3bb80.png">

到这里vps就做好了，进入下一步购买域名。

购买域名
买域名的地方也很多，国内主要是腾讯云和阿里云，域名不需要在国外供应商买，哪里买都一样。腾讯阿里都有新人优惠，第一次购买域名，像.club, .xyz之类的小众域名基本只要1块一年，很便宜了。我用的是腾讯云，这里也以腾讯云为例，其他平台的流程也基本一致。



首先进入腾讯云主页, 先点右上角的免费注册，注册登陆之后再产品这里选域名注册，热门里就有。

![1](https://user-images.githubusercontent.com/84239400/146675044-9849d760-ee2e-4667-93ea-38537a5b7138.png)

之后可以直接搜自己想要的域名，也可以直接点下面的1元域名优惠抢，首次注册都可以1块钱购买一年。（这里就不放图了，都是中文，应该很好操作了）

购买之后点右上角进入控制台，搜索云解析，进入这样一个界面。点击你自己的域名，或者点击右边域名对应的解析。（可以看到这里腾讯要求在国内开展网站需要备案，我们其实也相当于建立了一个网站，但是我的经验因为我们用国外的服务器所以不备案也没关系。）

![2](https://user-images.githubusercontent.com/84239400/146675048-c5a054cb-1b6e-47bd-962d-70e48d3760d7.png)

之后直接点击快速添加网站/邮箱解析，选择网站解析。之后输入刚才购买的vps的ip地址就好了，解析大概需要十分钟以内。

![3](https://user-images.githubusercontent.com/84239400/146675049-058f2101-a22e-442f-abb4-a3a458122592.png)

到这里域名购买解析部分就结束了，可以进行下一步，也是核心的一步，在vps上用脚本安装v2ray。

## 脚本安装v2ray服务端

首先下载一个ssh软件，比如putty，（我会放软件包度盘链接在下面，如果失效了就自己百度吧）打开软件是酱婶儿的。填进去你的ip然后open。

![4](https://user-images.githubusercontent.com/84239400/146675050-211dd1a6-9fe5-49bb-9174-601cf096bd28.png)

putty下载：
https://rachel.heartango.com/putty-64bit-0.73-installer.msi

然后用root账号登陆（注意login as 后面是填写用户名的，不是密码，先填用户名root回车再写密码，虽然好像很罗嗦，我之前也没想过这里也需要讲，但是真的有许多人卡在这一步），密码就是刚才记下的密码，输进去，敲回车。（注意这里可以直接把密码复制过去，但是一定注意第一不要复制到了空格，第二鼠标在putty里敲右键就是黏贴了，不要再ctrl+v，密码也是不会显示的，输进去直接回车就好）

进入命令行后，直接复制输入以下代码进行脚本安装。

```
curl -O https://raw.githubusercontent.com/luyiming1016/ladderbackup/master/v2ray_ws_tls.sh && chmod +x v2ray_ws_tls.sh && ./v2ray_ws_tls.sh
```

之后选1，回车，因为脚本需要安装Nginx，比较慢，大概五六分钟，等待一下。过程中会提示需要输入域名，输入解析到本VPS的域名，然后回车。
漫长等待之后，会出现安装完成的信息，然后会有配置参数，这里需要记下来（复制下来，在putty里左键光标选中的字符就是已经被复制了，不用ctrl+c了）。

到这时候，用任意一个浏览器输入你刚才注册的域名，应该就可以看到一个这样的网站。理解为它就是我们翻墙的掩护就好。

![5](https://user-images.githubusercontent.com/84239400/146675053-0e4b4c58-3d5c-4925-b275-4f716c7f88d4.png)

之后回到我们的putty界面，输入下面的代码安装BBR加速，安了会让科学上网速度提升很多。

```
cd /usr/src && wget -N --no-check-certificate "https://raw.githubusercontent.com/luyiming1016/ladderbackup/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```

在弹出的界面选1，安装内核，安装完之后vps会重启，putty会断开连接，重启等待1到2分钟，在重复刚才的步骤用putty登陆vps，输入以下代码，在弹出的界面输入5，使用BBR。

```
cd /usr/src && ./tcp.sh
```

之后显示BBR启动成功，这样我们服务端架设的步骤就完全完成了。
这时候注意最好在命令行输入service v2ray start，确保v2ray起来了，因为有时会发生系统重启v2ray进程起不来，会发生伪装网站可以进但配好不好用的状况

## 客户端使用
v2ray的客户端很多，这里主要介绍win，ios，安卓下最常用的三个客户端软件。

### Window使用v2ray

https://rachel.heartango.com/v2rayN-Core.zip

下载下来解压点进去文件夹，打开v2rayN.exe,右下角出现如下小图标：

![6](https://user-images.githubusercontent.com/84239400/146675055-47c1eaae-534f-4c01-b8ac-902c6c255fbd.png)

双击左键点开，选择服务器，添加vmess服务器。将之前在putty中记下的参数输入这里，如下图，然后点击确定。注意这里路径这一栏在之前记录的参数基础上前面加上“/”。如图。

![7](https://user-images.githubusercontent.com/84239400/146675056-71ff725e-c698-4588-b681-1bba500ef102.png)

之后就配置成功了，建议在配好的服务器上单击右键选择“批量导出分享URL至粘贴板”，然后在记事本中保存，之后会用在配置手机客户端里。

之后点右上角×关闭主界面，在右下角小图标单击右键。在服务器一栏勾选上已经配好的服务器，点击启用Http代理，代理模式选择全局模式。之后就可以开心的科学上网了。提醒一下记得不用的时候，按顺序先把启用http代理勾选取消，之后退出客户端，最后关电脑。如果有没有按顺序操作，再次开机发现上不了网了，请在这里的小电脑点右键，打开“网络和Internet设置”→代理→手动设置代理，将使用代理服务器一栏关闭。

### Mac使用v2ray
用法参考上面，逻辑差不多

https://rachel.heartango.com/V2rayU.dmg

### ios使用v2ray
其实V2ray在ios上最好用的客户端是Kitsunebi，可是在大陆App store里下不到，国外也是收费的。新版本的Shadowrocket也支持Vmess+TLS+ws的配置，所以我就用了Shadowrocket（以下就代称小火箭了），虽然小火箭也要钱，不能在大陆App store下载，但是网上共享账号很多，大家可以多搜一搜，关键词“Shadowrocket/小火箭 ios 共享账号”。我这里提供一组账号，大家试一试，不保证好用，因为这种多人共享的账号很容易被苹果封了，账号时效性很强，不好用大家就自己找找了（可以去万能的淘宝找，七八块一个带小火箭的共享账户）。

app store账号：hadadreammm@gmail.com
密码：As778899
注意下完小火箭后一定马上把账号退了，换回自己的账号。

之后把刚才在电脑端导出的，形如vmess://开头的链接复制到手机里，在手机上直接复制，然后打开小火箭，小火箭就会自动识别到已经复制好的链接，将服务器添加进来，之后把最上面的链接打开就好了。（软件会要求使用手机vpn，请允许）

### Android 使用v2ray
https://rachel.heartango.com/BifrostV_v0.6.8_apkpure.com.apk
使用方法和小火箭差不多，参考上面。
