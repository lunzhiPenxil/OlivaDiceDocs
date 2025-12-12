# 1.在一切的开始之前需知
OlivOS 青果核心交互栈，一个将各类涉及异步文本流交互的场景（即时通讯、直播弹幕、网络聊天室、静态命令行应用程序）转换到统一框架，基于统一流量管理、负载均衡、业务处理机制进行服务，以期在这些交互逻辑与功能需求类似的场景获得更加灵活的部署方式、更加有效的开发模式以及更加合理的资源调度。
## OlivOS的相关生态
`这意味着你能在以下地方找到OlivOS相关官方人员`

772730969 核心群

635811009 核心二群

472468101 核心三群

897924299 核心四群

828786809 青果用户群

1154204917 扩展分享群

796484814 OlivOS开发组（有严格的审核）

472635337 程心自定义交流群

青果论坛：
https://forum.olivos.run/

QQ频道：
https://qun.qq.com/qqweb/qunpro/share?_wv=3&_wwv=128&inviteCode=1lkjkb&from=246610&biz=ka

开黑啦：
https://kaihei.co/8orLDo

Dodo：
https://imdodo.com/i?gNo=75521

Fanbook：
https://fanbook.mobi/CW9VCF3l

Telegram：
https://t.me/+P0h50c7U9zQ2NmU1
## 关于框架和插件的部分

`OlivOS`是一款软件而一般称之为框架,其下的`OlivaDice`则是`OlivOS`的其中的插件,不应将`OlivOS`与`OlivaDice`混淆.


框架和插件不是平级关系      
而是上下级关系      
先有框架,再有插件在框架上运行,而常说的扩展则是和插件平级.

# 2.如何搭建OlivOS框架下的骰娘

> 更完善的指引请参考[【教程】手把手教你搭建青果骰](https://forum.olivos.run/d/25)  
> 注意：此教程的Windows搭建方法已过时，推荐使用Lagrange进行分离部署，请参考[【教程】小白可学的用 Lagrange.OneBot 对接 OlivOS](https://forum.olivos.run/d/705-lagrangeonebot-olivos/)  
> 或者进行LLOneBot的分离部署，请参考这篇教程：[【搬运-教程】新llob教程-小白可学的用 LLOneBot 对接 OlivOS](https://forum.olivos.run/d/835-llob-llonebot-olivos)  
> 又或者参考这个教程进行NapCat的分离部署：[【教程】小白可用的 OlivaDice 对接 NapCat 分离部署](https://forum.olivos.run/d/832-olivadice-napcat)  

在许多次版本迭代后,OlivOS的步骤已经简化到了有手就行的地步,但是不可能人人都是天才,总会有人需要帮助,因此也有了本文档.
## 那软件从哪里来呢?

这是一个好问题,首先需知,OlivOS是一款开源且免费的软件,这意味着,你从任何渠道,通过付费的方式获取到的软件,均非官方软件,那么从哪里获取到最新的且官方的OlivOS呢?在上面的所提供的OlivOS的相关生态中理论上都能获取到最新的OlivOS,如果都不行,你也可以通过访问GitHub上[OlivOS-Team的OlivOS](https://github.com/OlivOS-Team/OlivOS)的[releases](https://github.com/OlivOS-Team/OlivOS/releases)来获取本软件.
>啊这里有这么多可以下载的,我该选哪一个呢?

>这里就要看看命名方式了,举个栗子,OlivOS-Linux-0.11.7.zip这意味着,这个文件应该是Linux操作系统下的版本为0.11.7的ZIP包,Linux意味着是用于Linux系统的,而Win则是用于Windows系统的,Win-32则是32位的Windows系统

>如果你还是不知道你是哪个操作系统或者哪个这边建议点一下右边这个蓝色的链接[怎么查看自己电脑是什么操作系统](https://jingyan.baidu.com/article/1612d500e7c04fe20f1eee61.html)

当然,还有个方法,以源码方式运行,但是这表示你有相关Git与Github的使用知识,因此不说明.

好的,你现在有一个zip文件了,解压他,如果不会的话一样可以点一下右边这个蓝色的链接[如何解压缩Zip文件](https://zh.wikihow.com/%E8%A7%A3%E5%8E%8B%E7%BC%A9Zip%E6%96%87%E4%BB%B6)

## 2.1用于Windows系统的QQ机器人搭建

里面有一个名为OlivOS的文件和一个lib文件夹,单击那个名为OlivOS的文件![OlivOS文件图](/_static/OlivOS文件图.png)

就会有一个写着OlivOS登录器的东西弹出来

![OlivOS登录器](/_static/OlivOS登录器.png)

新建![新建](/_static/新建.png),会弹出一个

![OlivOS账号编辑器](/_static/OlivOS账号编辑器.png)

我们一行一行的看过来,账号类型,代表着你要选用什么平台来创建一个BOT,格式为 `平台名` - `以什么方式登录` - `登录协议`,这里暂时只提供`QQ`的创建方式,想知道另外的创建方法,可以去[论坛](forum.OlivOS.run)寻找其余软件的创建方式,或者加入OlivOS官方用户群与其他用户以及OlivOS官方获取相关方法.

再输入你的账号密码,点保存接着你的

![OlivOS登录器1](/_static/OlivOS登录器1.png)

就有了第一条内容,确认,就会弹出OlivOS的本体窗口![OlivOS终端](/_static\OlivOS终端.png),和GoCqhttp终端![GoCqhttp终端](/_static/GoCqhttp终端.png),到这里为止,恭喜你,你已经有独属于自己的`QQ`机器人了


## 2.2Linux下的部署      
说实话,你都用Linux了,我不太好说你需不需要这篇教学，但还是稍微讲一下流程吧,安装python,安装依赖,启动.sh结尾的文件,然后应该就可以了
 
这里有一份来自狐狐的[Linux手动安装OlivOS&Dice](https://www.aobacore.com/archives/OlivOS-OlivaDice-Go-cqhttp.html)      


>那我不管对他输啥,他怎么没反应呢?

>因为OlivOS是个框架,用建房子来举例子,OlivOS就是地基,而插件才是房子本体,睡地基上也不是不行,但是买了房子总不能睡地基上让施工队别施工吧.
## 插件的安装
OlivOS有非常多官方插件，如OlivaDiceCore，ChanceCustom，OlivaDiceJoy，OlivaDiceLogger，OlivaDiceMaster，OlivaDiceOdyssey不排除以后会有更多的情况
讲道理如果你下的是整合包，可以先看看在`\plugin\app\`下有没有任何以OPK结尾的文件
如果没有，你可以前往论坛获取文件[OlivOS论坛](https://forum.olivos.run/)
放置在`\plugin\app\`路径下，
每一个OPK文件都是一个插件
      
# 结束
欢迎使用OlivOS
