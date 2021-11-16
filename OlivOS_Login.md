# OlivaDice For OlivOS 启程手册

## 获取软件
你可以从一下页面获取链接：  
[青果云](http://pan.benzencloudhk.xyz/s/ex9uwmsh)   密码：`LOVEOLIVA`  
[Github](https://github.com/OlivOS-Team/OlivaDiceCore/releases)  

下载后解压并双击运行`OlivOS.exe`，稍加等待便会弹出登录窗口。  

![DIXE(OLIVADICE)](_static/OlivOS_Login_001.png)

## 登录指引
OlivOS目前支持`QQ`、`Telegram`、`Dodo`、`Fanbook`  
登录窗口如下，单击`NEW`即可添加新账号  

![DIXE(OLIVADICE)](_static/OlivOS_Login_002.png)

### QQ
> 警告：
> 
> 1. 以下的操作将使用[go-cqhttp](https://github.com/Mrs4s/go-cqhttp)作为第三方客户端进行登录。
> 2. 因为违反QQ用户协议造成的损失，后果自负。

你需要像如下方式进行设置，然后单击`SAVE`进行保存  

![DIXE(OLIVADICE)](_static/OlivOS_Login_003.png)

### Dodo
> 警告：
> 
> 1. 以下的操作说明将默认以你使用Chrome浏览器在网页端登录。
> 2. 按照以下操作登录前，你需要事先准备好一个账号。

你需要像如下方式进行设置，然后单击`SAVE`进行保存  

![DIXE(OLIVADICE)](_static/OlivOS_Login_004.png)

为了获取上图中的相关参数，你需要将事先准备好的账号在[DoDo Web](https://dodo.link)上登录。

DoDo网页版暂时只支持手机短信验证码和微信扫码两种登录方式，建议你创建一个小号来进行登录。

完成登录后，请在浏览器打开`开发人员工具`，导航到`应用程序（Application） -> 存储（Storage） -> 本地存储（Local Storage） -> https://dodo.link`。
成功登录的情况下，你将在右侧的`key`列找到如下两个你需要的参数：

1. `uid`
2. `token`

`token`有7天有效期，请放心，OlivOS会自动延长它的有效期。

![DIXE(OLIVADICE)](_static/OlivOS_Login_006.png)

### Fanbook

你需要像如下方式进行设置，然后单击`SAVE`进行保存  

![DIXE(OLIVADICE)](_static/OlivOS_Login_005.png)

你可以通过Fanbook官方的`机器人管家`申请机器人账号，你将获得一个Token

![DIXE(OLIVADICE)](_static/OlivOS_Login_007.png)

## 文件结构
目前较为关键的配置文件如下所示

![DIXE(OLIVADICE)](_static/OlivOS_Login_008.png)

对应每个Bot账号的文件路径为`plugin/data/OlivaDice/{botHash}/`  
当`{botHash}`为`unity`时，配置对所有Bot生效  

 - 牌堆路径为`plugin/data/OlivaDice/{botHash}/extend/deckclassic/`
 - 帮助文档路径为`plugin/data/OlivaDice/{botHash}/extend/helpdoc/`
 - 自定义回复词路径为`plugin/data/OlivaDice/{botHash}/console/customReply.json`
 - 关键设置配置路径为`plugin/data/OlivaDice/{botHash}/console/switch.json`

