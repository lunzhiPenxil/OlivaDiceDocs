# OlivaDice For OlivOS 启程手册

> 更完善的指引请参考[【教程】手把手教你搭建青果骰](https://forum.olivos.run/d/25)

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
请注意，你需要在搭建的过程中将你所搭建的小号上报给dodo官方，详情参考该频道
https://www.imdodo.com/channel/108078/130977

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

### 关键设置配置 | switch.json
```json
{
    "globalEnable": 1,
    "userConfigCount": 100,
    "autoAcceptGroupAdd": 1,
    "autoAcceptFriendAdd": 1,
    "masterList": [
        [
            123456789,
            "qq"
        ],
        [
            123456789123456789,
            "telegram"
        ]
    ],
    "noticeGroupList": [
        [
            987654321,
            "qq"
        ],
        [
            123456789123456789,
            "telegram"
        ]
    ],
    "pulseUrlList": [
        [
            "https://api.dice.center/dicestatusup/",
            "YUXIANXIAGUOYUXIANXIAGUO"
        ]
    ]
}
```

### 自定义回复词 | customReply.json
```json
{
    "strSetStr": "回复词[{tStrName}]已更新",
    "strBecomeMaster": "口令正确，[{tName}]已成为Master",
    "strCantBecomeMaster": "口令错误，拒绝认证",
    "strMasterConsoleShow": "[{tConsoleKey}]当前为[{tConsoleValue}]",
    "strMasterConsoleSet": "[{tName}]已将[{tConsoleKey}]设置为[{tConsoleValue}]",
    "strMasterConsoleSetInvalid": "非法的配置值",
    "strMasterConsoleNotFound": "无法访问的配置项",
    "strNeedMaster": "需要Master权限",
    "strHello": "欢迎使用本机器人! 请使用[.help]查看帮助",
    "strBot": "欢迎使用本机器人! 请使用[.help]查看帮助",
    "strBotExit": "即将退出本群",
    "strBotExitRemote": "收到远程控制, 即将退出本群",
    "strBotExitRemoteShow" : "即将远程退出群[{tGroupId}]",
    "strBotAddFriendNotice": "好友添加请求, 来自[{tUserId}]\n备注:{tComment}\n{tResult}",
    "strBotAddGroupNotice" : "群添加请求，来自群[{tGroupId}], 邀请者[{tInvaterId}]\n{tResult}",
    "strBotAddGroupNoticeIgnoreResult" : "已忽略\n请输入[{tAcceptCommand}]以远程接受请求",
    "strBotAddGroupRemoteAcceptShow" : "已远程接受请求[{tInvateFlag}]",
    "strAccept" : "已接受",
    "strIgnore" : "已忽略",
    "strReject" : "已驳回",
    "strBotOn" : "开启成功",
    "strBotAlreadyOn" : "已经处于开启状态",
    "strBotOff" : "关闭成功",
    "strBotAlreadyOff" : "已经处于关闭状态",
    "strBotNotUnderHost" : "无所属主频道",
    "strBotHostLocalOn" : "本主频道开启成功",
    "strBotAlreadyHostLocalOn" : "本主频道已经处于开启状态",
    "strBotHostLocalOff" : "本主频道关闭成功",
    "strBotAlreadyHostLocalOff" : "本主频道已经处于关闭状态",
    "strBotHostOn" : "本主频道进入默认开启模式",
    "strBotAlreadyHostOn" : "本主频道已经处于默认开启模式",
    "strBotHostOff" : "本主频道进入默认关闭模式",
    "strBotAlreadyHostOff" : "本主频道已经处于默认关闭模式",
    "strHelpDoc" : "已为你找到以下以下条目:\n{tHelpDocResult}",
    "strHelpDocRecommend" : "已为你找到以下以下相似条目:\n{tHelpDocResult}",
    "strHelpDocNotFound" : "未找到匹配条目",
    "strDrawTi" : "[{tName}]疯狂发作-临时症状:\n{tResult}",
    "strDrawLi" : "[{tName}]疯狂发作-总结症状:\n{tResult}",
    "strDrawName" : "[{tName}]的随机名称:\n{tResult}",
    "strDrawDeck" : "你抽到了:\n{tDrawDeckResult}",
    "strDrawDeckHideShow" : "[{tName}]进行了暗抽牌",
    "strDrawDeckNotFound" : "牌堆未找到",
    "strRoll" : "[{tName}]掷骰: {tRollResult}",
    "strRollWithReason" : "[{tName}]由于[{tRollReason}]掷骰: {tRollResult}",
    "strRollHide" : "于群[{tGroupId}]中[{tName}]掷骰: {tRollResult}",
    "strRollHideWithReason" : "于群[{tGroupId}]中[{tName}]由于[{tRollReason}]掷骰: {tRollResult}",
    "strRollHideShow" : "[{tName}]掷暗骰",
    "strRollHideShowWithReason" : "[{tName}]由于[{tRollReason}]掷暗骰",
    "strRollRange" : "表达式: {tRollPara}\n细节: {tRollResultDetail}\n结果: {tRollResultInt}\n范围: {tRollResultIntRange}",
    "strPcInit" : "[{tPcTempName}]人物卡作成:{tPcInitResult}",
    "strPcUpdateSkillValue" : "[{tName}]的人物卡已更新:\n[{tSkillName}]: {tSkillUpdate}",
    "strPcSetSkillValue" : "[{tName}]的人物卡已保存",
    "strPcGetSingleSkillValue" : "[{tName}]的[{tSkillName}]: {tSkillValue}",
    "strPcShow" : "人物卡[{tName}]:\n{tPcShow}",
    "strPcList" : "[{tName}]的人物卡:\n{tPcList}\n当前选择:{tPcSelection}",
    "strPcSet" : "人物卡已切换至[{tPcSelection}]",
    "strPcSetError" : "试图切入的人物卡不存在",
    "strPcDel" : "人物卡[{tPcSelection}]已删除",
    "strPcDelError" : "试图删除的人物卡不存在",
    "strPcTemp" : "人物卡[{tPcSelection}]套用模板[{tPcTempName}]",
    "strPcTempShow" : "人物卡[{tPcSelection}]:\n模板[{tPcTempName}]",
    "strPcTempError" : "试图套用的模板不存在，或是未设置人物卡",
    "strPcTempRule" : "人物卡[{tPcSelection}]套用模板[{tPcTempName}]的规则[{tPcTempRuleName}]",
    "strPcTempRuleShow" : "人物卡[{tPcSelection}]:\n模板[{tPcTempName}]\n规则[{tPcTempRuleName}]",
    "strPcTempRuleError" : "试图套用的模板规则不存在，或是未设置人物卡",
    "strPcRename" : "[{tPcSelection}]已重命名为[{tPcSelectionNew}]",
    "strPcSkillCheck" : "[{tName}]进行技能[{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHide" : "于群[{tGroupId}]中[{tName}]进行技能[{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideShow" : "[{tName}]进行技能[{tSkillValue}]暗检定",
    "strPcSkillCheckWithSkillName" : "[{tName}]进行技能[{tSkillName}:{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideWithSkillName" : "于群[{tGroupId}]中[{tName}]进行技能[{tSkillName}:{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideShowWithSkillName" : "[{tName}]进行技能[{tSkillName}:{tSkillValue}]暗检定",
    "strSanCheck" : "[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}点,当前剩余[{tSkillValueNew}]点",
    "strSanCheckGreatFailed" : "[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}的最大值[{tRollSubResultIntMax}]点,当前剩余[{tSkillValueNew}]点",
    "strIntPositiveInfinite" : "正无穷大",
    "strIntNegativeInfinite" : "负无穷大",
    "strPcSkillCheckSucceed" : "成功",
    "strPcSkillCheckHardSucceed" : "困难成功",
    "strPcSkillCheckExtremeHardSucceed" : "极难成功",
    "strPcSkillCheckGreatSucceed" : "大成功",
    "strPcSkillCheckFailed" : "失败",
    "strPcSkillCheckGreatFailed" : "大失败",
    "strPcSkillCheckFate01" : "[-2 拙劣]",
    "strPcSkillCheckFate02" : "[-1 差劲]",
    "strPcSkillCheckFate03" : "[+0 二流]",
    "strPcSkillCheckFate04" : "[+1 一般]",
    "strPcSkillCheckFate05" : "[+2 尚可]",
    "strPcSkillCheckFate06" : "[+3 良好]",
    "strPcSkillCheckFate07" : "[+4 极佳]",
    "strPcSkillCheckFate08" : "[+5 卓越]",
    "strPcSkillCheckFate09" : "[+6 惊异]",
    "strPcSkillCheckFate10" : "[+7 史诗]",
    "strPcSkillCheckFate11" : "[+8 传奇]",
    "strPcSkillCheckNope" : "需要解释",
    "strPcSkillCheckError" : "发生错误"
}
```
