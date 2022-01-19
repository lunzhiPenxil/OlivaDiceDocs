# 前置基础知识
## 关于框架和插件的部分
首先知悉一点        
框架和插件不是平级关系      
而是上下级关系      
先有框架,再有插件在框架上运行   

至于扩展那是插件的事情,和框架无关   
以下是常见的    
OlivaDiceCore,溯洄核心,铃心等插件     
OlivOS,Mirai,XQ等框架的支持图表 

|插件|OlivOS<br>简写:OvO<br>直接运行| Mirai<br>学名:未来<br>需要native | XQ<br>学名:先驱<br>需要额外插件转接 |
| - | - | - | - |
| OlivaDiceCore | √ | × | × |
| 溯系核心 | × | √ | √ |
| 铃心 | × | √ | √ |

## 关于骰娘核心的部分
这一段在其他地方    
已经有详细的叙述了    
本篇不多赘述

# 如何搭建OvO框架下的骰娘
# 1.选择你的系统和运行方式
* windows(不一一列举)
    1. 以源码形式运行   
        * 需要手动安装依赖  
        是源码运行
        适合进阶玩家    
        支持更多依赖（毕竟自己手动配置）
    2. 以整合包方式运行
        * 一键安装  
        是exe运行   
        适合新手玩家    
        对于更多依赖暂时还不支持    
* linux(不一一列举)
    1. 以源码形式运行
        * linux目前没有一键包   
        需要手动安装依赖  
        需要手动配置    
        是源码运行
        适合进阶玩家    
        支持更多依赖（毕竟自己手动配置）

> 如果不喜欢看上面那一大段东西  
> 那么请至少看这个表格

| 系统 | 运行方式 | 配置gcq | 手动装依赖 |
| - | - | - | - |
| Windows | exe | × | × |
| Windows | 源码 | × | √ |
| linux | 源码 | √ | √ |

# 2.部署与运行OvO框架
## Windows下的基础文件部署
###  以整合包进行基础文件部署
0. 将整个整合包解压到你想要的文件夹里去         
建议路径全英文，中文也行
1. 观察是否满足整合包要求
    1. 在整合包的`根目录`下有一个`OlivOS.exe`
    2. 在整合包的`lib`目录下有一个`go-cqhttp.exe`
    3. 在整合包的`plugin\app`目录下有一个`OlivaDiceCore`的文件夹或者`.opk`文件
    4. 如果以上条件满足,请开始下一步    
    否则请换一个整合包    
    或者参考Win的以`源码模式运行`章节     
    进行资源文件补齐
2. 在满足上述要求后,观看后面的运行章节    

### 以源码模式进行基础文件部署
1. **基础条件**      
    1.  能直接访问`Github`      
    或者会使用各种镜像站下载    
    2. 有Chrome,FireFox,Edge等     
    任意一种常见的Chrome内核浏览器    
    这个不作强制要求,但是推荐使用   
    防止因为浏览器原因导致的无法打开Github
2. **开始安装**     
    1. 你需要安装python3.7.5以上版本     
        Python官网下载地址:https://www.python.org/downloads/    
        安装过程请记得将添加环境变量(Add Python 3.xx to PATH)的√勾上     
    2. 从`Github`下载[OlivOS-Team/OlivOS](https://github.com/OlivOS-Team/OlivOS)（OlivOS框架）源码      
    3. 解压到你喜欢的文件夹/路径下面    
    这里假设你放在了`D:\OlivOS`路径下   
    在此路径下能直接看见`main.py`
    4. 安装requirements依赖     
        1. 打开cmd输入以下指令然后执行     
        `cd D:\OlivOS && pip install -r requirements.txt`   
        * 如果下载速度缓慢请自行切换镜像站下载，例：  
            `cd D:\OlivOS && pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple/`      
            * 想要通过不同的镜像站进行下载    
            请自行通过搜索引擎寻找更多镜像站（如Baidu,Google）    
        2. 或者在`scrpits\`目录下找到`install.bat`来安装依赖    
        如果安装缓慢可以尝试第一步的第二种方法
    5. 从`Github`下载[OlivOS-Team/OlivaDiceCore](https://github.com/OlivOS-Team/OlivaDiceCore)（OlivaDiceCore）源码    
        * 下载完成后解压压缩包里的`OlivaDiceCore`到   
        `D:\OlivOS\plugin\app\`路径下   
        * 完整路径应该是`D:\OlivOS\plugin\app\OlivaDiceCore\`     
        而且打开后能直接看见`main.py`   
        * 如果不是,可能是你的文件夹套娃了     
        请剪切出来      
        或者从[releases](https://github.com/OlivOS-Team/OlivaDiceCore/releases/)直接下载以.opk结尾的插件
        * 下载完成后直接放在`D:\OlivOS\plugin\app\`路径下
    5. 从`Github`的`go-cqhttp/releases`下载[go-cqhttp_windows_amd64.exe](https://github.com/Mrs4s/go-cqhttp/releases)     
        * 如果有qq平台账号登录需求    
        * 或者通过整合包复制一个过来
        * 下载完成后放在`lib`目录下 
        * 重命名`go-cqhttp_windows_amd64.exe`为`go-cqhttp.exe`      
    7. 观看后面的运行章节

### Win环境的第一次运行
**前置要求**    
看到这里    
那么就已经按照上面的手册操作过了    
环境,依赖,gcq,插件什么的都装完放对位置了    
那么开始下一步,启动

**启动**    
这里有两种运行方式   
自己寻找对应的运行方式即可
这里假设你主路径是`D:\OlivOS`    
1. 通过整合包的exe运行
    1. 直接双击OlivOS.exe
2. 通过源码运行
    1. 第一种方式：   
      直接使用自带启动脚本           
      进入`D:\OlivOS\scripts\`文件夹   
      直接运行`start.bat`即可  
    2. 第二种方式：手打指令       
      Win+R    
      在弹出的窗口输入cmd     
      点击确定    
      输入`python D:\OlivOS\main.py`    

**第一次登录**  
请观看[Oliva|3启程手册](https://wiki.dice.center/OlivOS_Login.html)

## Linux下的基础环境部署    
### 以源码模式进行基础文件部署  
这里有一份来自狐狐的[Linux手动安装OlivOS&Dice](https://www.aobacore.com/archives/OlivOS-OlivaDice-Go-cqhttp.html)   


# 3.关于骰娘的拓展
（如果需要jrrp，draw，helpdoc等非OlivaDiceCore本身有的功能请看此条）
    从`Github`下载[OlivOS-Team/OlivaDiceJoy](https://github.com/OlivOS-Team/OlivaDiceJoy)源码，或者从[releases](https://github.com/OlivOS-Team/OlivaDiceJoy/releases/) 直接下载opk结尾的插件   
    放置在`D:\OlivOS\plugin\app\`路径下
    
# 4.登录完毕以后的各项基础配置
## Win下取消登录时候的commit框
1. 删除`conf\basic.json`里第七行的  
`"OlivOS_multiLoginUI",`    
所在的一整行
2. 如果想要继续添加这个框就把这一行加回去

## Win下设置登录时候的不同平台怎么设置
1. 选择Platform     
2. 自行选择你想要使用的平台对应的项目

## Win下设置登录的时候的保存
1. token必须要填    
    * 其他平台请按照[Oliva|3启程手册](https://wiki.dice.center/OlivOS_Login.html)里的方式寻找对应的token
    * qq平台例外    
    可以填任意字符上去，比如说填一个`1`     
    当然也可以将`Auto`改为`True`    
    那样会由`OvO框架`自动为您生成此账号的hash当token
2. 不知道`Host`和`Port`填啥就将`Auto`改为`True`     
    再点击`Save`    
    保存完以后再通过`Edit`自行修改`Port`端口号      
    当然不改端口号也行

## 各种常见的骰娘配置疑问
1. 怎么设置master
    1. 在OlivOS控制台可以看见如[.master xxxxxxxx-xxxx-xxxxx-xxxxxx-xxxxxxxx]类似的语句。
    2. 在私聊窗口向骰娘发送这一句
2.如何确认你已经是master了
    1. 在`OlivOS\plugin\data\OlivaDice\{bot_hash}\console`目录下   
    有个switch.json文件，以文本文档的形式打开，应该会有你的QQ号    
    2. {bot_hash}就是形如`098f6bcd4621d373cade4e832627b4f6`的文件夹名称

# 5.关于手动配置go-cqhttp的那些事
## 写在前面的：    
目前qq平台的发消息机制如下：    
由`go-cqhttp`获取来自腾讯服务器的消息转发给`OlivOS`   
`OlivOS`上加载的插件处理完毕以后    
由`OlivOS`发送给`go-cqhttp`   
再由go-cqhttp发送给腾讯服务器   

> 所以需要同时调整OlivOS和go-cqhttp的设置

## 需要配置的文件所在位置
此处约定~1为`OlivOS`框架所在路径     
~2为`go-cqhttp`所在路径     

| · | 文件名 | 所在文件夹位置 |
| - | - | - |
| OlivOS | account.json | ~1\conf\account.json |
| OlivOS | basic.json | ~1\conf\basic.json |
| go-cqhttp | config.yml | ~2\config.yml |

假设你是win系统     
~1为`D:\OlivOS\`        
~2为`D:\OlivOS\lib\`        
那么对应的文件路径分别为        
D:\OlivOS\conf\account.json     
D:\OlivOS\conf\basic.json       
D:\OlivOS\lib\config.yml        

## 配置之前需要做的
1. OlivOS
    1. 运行OlivOS   
        >(linux用户可以考虑先windows上生成一个以后复制过去,或者熟记结构以后手搓)   
    2. 按照正常流程设置一遍虚拟账号密码     
    比如账号为`1`,密码为`1`     
    设置`auto`,设置`qq`,`onebot`     
    点击`save`,此时应当看见一个已经保存成功的账号为`1`的条目    
    点击`commit`
    3. 关闭`OlivOS`,此时已经生成填写模板了
2. go-cqhttp
    1. 运行go-cqhttp 
    2. 选择0 - HTTP

## 详细配置环节
所需要配置的文件有三个
1. OlivOS(框架)  
    1. account.json（文件）
        1. id：输入你的骰娘qq
        2. password：随便填，或者不填也行   
        账号密码核心设置在go-cqhttp那
        3. server
            1. host:你的go-cqhttp所在ip  
            如果是本机可填127.0.0.1     
            你接收完消息,处理完毕以后   
            需要发到go-cqhttp上去   
            然后交由go-cqhttp发送到腾讯聊天服务器上去
            2. port:端口号，与go-cqhttp上设置的一致
            3. access_token:随意编造一个    
            建议设置的复杂一点  
            这个可以类比成和go-cqhttp通讯时的密码
    2. basic.json（文件）
        1. models
            1. OlivOS_flash_post_rx
                1. server
                    1. port     
                    设置端口号   
                    推荐自动以后改手动
                    2. host就默认0.0.0.0好了  
2. go-cqhttp(运行文件)    
    1. config.yml（文件）
        1. account  
            1. uin: 输入你的骰娘qq,和上面的一致
            2. password就留空,扫码登录就好
        2. default -middlewares
            1. access-token：这个的填写和`access_token`一致    
            **在OlivOS发送给gcq的时候gcq会根据这个来鉴权     
            所以请务必保证这个密钥的强度够高**
        3. servers
            1. http
                1. host：填写你go-cqhttp运行服务器所在ip    
                如果就是本机的话可以直接输入localhost   
                如果是远程请务必不要使用localhost或者127.0.0.1  
                请填写你自己的服务器ip地址      
                否则回复消息无法送达    
                    >**举例一：**    
                    A服务器ip为`192.168.1.10`，运行OlivOS     
                    B服务器ip为`192.168.1.11`，运行go-cqhttp     
                    B服务器此处应当填写的是`192.168.1.11`     
                    或者`0.0.0.0`   
                    ……………分割线…………………    
                    **举例二：**      
                    A服务器ip为`192.168.1.3`      
                    同时运行OlivOS和go-cqhttp   
                    那么只要填`127.0.0.1`就好了   
                    ……………分割线…………………
                    简单来说就是    
                    如果你的OlivOS和go-cqhttp不在同一个ip上     
                    请参照举例一    
                    如果在同一个电脑上  
                    请参照举例二
                2. port：
                    1. 这个port和上面`account.json`里的`port`保持一致   
                    否则无法通信
                2. secret目前似乎不需要填写     
                等待纠正中  
                (疑似是发给OlivOS的时候让OlivOS鉴权用的)
