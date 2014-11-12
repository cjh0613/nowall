# nowall, no wall & now all

------

所处特殊之环境，我等码农人士一个必备技能就是Flew Over GFW，俗称*翻---墙*。虽然也花钱买过不少vpn工具，但发现Z*F还是很强大地，很难有哪个vpn可以长期快速稳定，至于免费的翻墙工具那更是只能蹦跶几天，时不时的就要花时间找能用的代理或者vpn，简直是烦透了，也太浪费时间！

吐槽这么多，就是要道出**nowall**的由来：窃以为只有每个人使用自己独立的代理服务器，才有可能有长久的生命力，这样没有形成规模，人家也就不屑于理咱这小喽啰了！ Goagent走的就是这样的路子，只是它过于依赖GAE，导致goagent过段时间就得升级一次，稍嫌麻烦，所以很久也没用goagent了，不知它现在怎样，尚能饭否？

**nowall**预期目标是支持各个平台，这样可供我们选择的免费空间也就更多些。

下边是**nowall**的一些特性：
> 1.支持http及https请求的的代理
> 2.服务端代理同时提供http和https两种协议，需要补充的是https实际上使用的是**spdy**协议（[google推出的一种协议](http://zh.wikipedia.org/zh/SPDY)），所以理论上说速度应该更快，比https那是铁板钉钉的快，比http尚有争论。 当然使用它的前提是您的服务器要允许你https访问。
> 3.支持代理服务器的cdn加速访问。 这个就基本可以解决一些云平台被封的问题，例如加速我们的代理服务端部署在GAE上，那如果我们有自己的域名的话，就可以通过CDN站点指向我们的GAE服务器，继而就可以通过这个域名访问了。

目前nowall支持代理http和https访问，但代码还要进一步优化。

下边是下一步计划：

> * ~~研究websocket,SPDY协议，考虑使用这些协议优化代理连接速度。~~(已完成)
> * 开发其他语言的nowall服务端版本，以期支持更多服务器。
> * 各平台的文档完善

------

## 通用部署简单说明
###服务端
使用nowall前，您需要准备好一个可以访问国外网站的服务器，目前由于服务端只有node.js版本的，所以您的服务器需要支持node.js。
之后您只需要将代码中的server/node.js文件夹下的内容upload到您的服务器，运行server.js即可，当然您也许需要修改config.json来修改代理端口。

###客户端
> * 第一版毫无疑问，您得先安装好node.js
> * 为支持https访问，本程序模拟goagent的原理，在本地会生成证书，所以您需要在 本地安装好openssl，安装方法可以参考相关教程，安装完成后您应该可以在打开命令行后执行openssl得到正确的反馈。
同时您需要将local文件夹下的ca.crt导入到您浏览器的根目录，您可能问我如何保证这个证书的安全，说实话我也没办法保证，所以您不怕麻烦的话就自己生成ca.key和ca.crt覆盖我提供的也可以。
> * 最后打开local文件夹，修改config.json,运行start.js。

然后在浏览器上配置上http代理，即可正常使用, chrome推荐使用Switchy!，极端好用！


最后感谢https://www.zybuluo.com/mdeditor   提供这么好的工具，使我可以迅速的写出一个md文件！