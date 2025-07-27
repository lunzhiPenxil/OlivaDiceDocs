# OlivaDice For OlivOS 启程手册

> 更完善的指引请参考[【教程】手把手教你搭建青果骰](https://forum.olivos.run/d/25)  
> 注意：此教程的Windows搭建方法已过时，推荐使用Lagrange进行分离部署，请参考[【教程】小白可学的用 Lagrange.OneBot 对接 OlivOS](https://forum.olivos.run/d/705-lagrangeonebot-olivos/)  
> 或者参考上面Lagrange的搭建教程进行[LLOneBot](https://llonebot.com/zh-CN/guide/getting-started)的分离部署  

## 获取软件
你可以从一下页面获取链接：  
[青果云](http://pan.benzencloudhk.xyz/s/ex9uwmsh)   密码：`LOVEOLIVA`  
[Github](https://github.com/OlivOS-Team/OlivaDiceCore/releases)  

下载后解压并双击运行`OlivOS.exe`，稍加等待便会弹出登录窗口。  

![DIXE(OLIVADICE)](/_static/OlivOS_Login_001.png)

## 登录指引
OlivOS目前支持`QQ`、`Telegram`、`Dodo`、`Fanbook`  
登录窗口如下，单击`NEW`即可添加新账号  

![DIXE(OLIVADICE)](/_static/OlivOS_Login_002.png)

### QQ
> 警告：
> 
> 1. 以下的操作将使用[go-cqhttp](https://github.com/Mrs4s/go-cqhttp)作为第三方客户端进行登录。
> 2. 因为违反QQ用户协议造成的损失，后果自负。

你需要像如下方式进行设置，然后单击`SAVE`进行保存  

![DIXE(OLIVADICE)](/_static/OlivOS_Login_003.png)

### Dodo
> 警告：
> 
> 1. 以下的操作说明将默认以你使用Chrome浏览器在网页端登录。
> 2. 按照以下操作登录前，你需要事先准备好一个账号。

你需要像如下方式进行设置，然后单击`SAVE`进行保存  

![DIXE(OLIVADICE)](/_static/OlivOS_Login_004.png)

为了获取上图中的相关参数，你需要将事先准备好的账号在[DoDo Web](https://dodo.link)上登录。

DoDo网页版暂时只支持手机短信验证码和微信扫码两种登录方式，建议你创建一个小号来进行登录。
请注意，你需要在搭建的过程中将你所搭建的小号上报给dodo官方，详情参考该频道
https://www.imdodo.com/channel/108078/130977

完成登录后，请在浏览器打开`开发人员工具`，导航到`应用程序（Application） -> 存储（Storage） -> 本地存储（Local Storage） -> https://dodo.link`。
成功登录的情况下，你将在右侧的`key`列找到如下两个你需要的参数：

1. `uid`
2. `token`

`token`有7天有效期，请放心，OlivOS会自动延长它的有效期。

![DIXE(OLIVADICE)](/_static/OlivOS_Login_006.png)

### Fanbook

你需要像如下方式进行设置，然后单击`SAVE`进行保存  

![DIXE(OLIVADICE)](/_static/OlivOS_Login_005.png)

你可以通过Fanbook官方的`机器人管家`申请机器人账号，你将获得一个Token

![DIXE(OLIVADICE)](/_static/OlivOS_Login_007.png)

## 文件结构
目前较为关键的配置文件如下所示

![DIXE(OLIVADICE)](/_static/OlivOS_Login_008.png)

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
    "strBotName": "Bot",
    "strForGroupOnly": "此功能仅对群聊开放",
    "strSetStr": "回复词[{tStrName}]已更新",
    "strBecomeMaster": "口令正确，[{tUserName}]已成为Master",
    "strBecomeMasterAlready": "你已经拥有Master权限，无需再次认证",
    "strCantBecomeMaster": "无Master权限且口令错误，拒绝认证",
    "strMasterSystemRestart": "[{tUserName}]远程调用重载",
    "strMasterConsoleShow": "[{tConsoleKey}]当前为[{tConsoleValue}]",
    "strMasterConsoleShowList": "[{tConsoleKey}]当前为:\n{tConsoleValue}",
    "strMasterConsoleSet": "[{tUserName}]已将[{tConsoleKey}]设置为[{tConsoleValue}]",
    "strMasterConsoleAppend": "[{tUserName}]已修改[{tConsoleKey}]条目",
    "strMasterConsoleSetInvalid": "非法的配置值",
    "strMasterConsoleNotFound": "无法访问的配置项",
    "strMasterRemoteOn": "已在[{tId}]远程开启",
    "strMasterRemoteOff": "已在[{tId}]远程关闭",
    "strMasterRemoteOnAlready": "[{tId}]已处于开启状态",
    "strMasterRemoteOffAlready": "[{tId}]已处于关闭状态",
    "strMasterRemoteDefaultOn": "已在[{tId}]远程默认开启",
    "strMasterRemoteDefaultOff": "已在[{tId}]远程默认关闭",
    "strMasterRemoteDefaultOnAlready": "[{tId}]已处于默认开启状态",
    "strMasterRemoteDefaultOffAlready": "[{tId}]已处于默认关闭状态",
    "strMasterRemoteNone": "设置失败，未找到[{tId}]的相关记录",
    "strAddCensor": "敏感词已添加",
    "strDelCensor": "敏感词已移除",
    "strCensorReplace": "*",
    "strNeedMaster": "需要Master权限",
    "strNeedAdmin": "需要管理员以上权限",
    "strWelcomeSet": "欢迎词已设置",
    "strWelcomeDel": "欢迎词已清除",
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
    "strHelpDoc" : "已为你找到以下条目:\n{tHelpDocResult}",
    "strHelpDocRecommend" : "已为你找下相似条目:\n{tHelpDocResult}",
    "strHelpDocNotFound" : "未找到匹配条目",
    "strDrawTi" : "[{tName}]疯狂发作-临时症状:\n{tResult}",
    "strDrawLi" : "[{tName}]疯狂发作-总结症状:\n{tResult}",
    "strDrawName" : "[{tName}]的随机名称:\n{tResult}",
    "strDrawDeck" : "你抽到了:\n{tDrawDeckResult}",
    "strDrawDeckHideShow" : "[{tName}]进行了暗抽牌",
    "strDrawDeckRecommend" : "已为你找到以下相似牌堆:\n{tDrawDeckResult}",
    "strDrawDeckNotFound" : "牌堆未找到",
    "strRollRecord" : "按照[{tRollFormatType}]重新显示的上次掷骰:\n{tRollResult}",
    "strRoll" : "[{tName}]掷骰: {tRollResult}",
    "strRollWithReason" : "[{tName}]由于[{tRollReason}]掷骰: {tRollResult}",
    "strRollHide" : "于群[{tGroupId}]中[{tName}]掷骰: {tRollResult}",
    "strRollHideWithReason" : "于群[{tGroupId}]中[{tName}]由于[{tRollReason}]掷骰: {tRollResult}",
    "strRollHideShow" : "[{tName}]掷暗骰",
    "strRollHideShowWithReason" : "[{tName}]由于[{tRollReason}]掷暗骰",
    "strRollRange" : "表达式: {tRollPara}\n细节: {tRollResultDetail}\n结果: {tRollResultInt}\n范围: {tRollResultIntRange}",
    "strRollError01" : "表达式[{tRollPara}]掷骰错误！无法解析的表达式！",
    "strRollError02" : "表达式[{tRollPara}]掷骰错误！无法计算的表达式！",
    "strRollError03" : "表达式[{tRollPara}]掷骰错误！输入了非法的表达式！",
    "strRollError04" : "表达式[{tRollPara}]掷骰错误！输入了非法的子参数！",
    "strRollError05" : "表达式[{tRollPara}]掷骰错误！输入了非法的运算符！",
    "strRollError06" : "表达式[{tRollPara}]掷骰错误！发现未定义运算符！",
    "strRollError07" : "表达式[{tRollPara}]掷骰错误！解析到空语法树！",
    "strRollError08" : "表达式[{tRollPara}]掷骰错误！错误的左值！",
    "strRollError09" : "表达式[{tRollPara}]掷骰错误！错误的右值！",
    "strRollError10" : "表达式[{tRollPara}]掷骰错误！错误的子参数！",
    "strRollError11" : "表达式[{tRollPara}]掷骰错误！计算极值时出错！",
    "strRollError12" : "表达式[{tRollPara}]掷骰错误！解析技能变量时出错！",
    "strRollErrorUnknown" : "表达式[{tRollPara}]掷骰错误！未知的错误: {tResult}",
    "strRollErrorHelp" : "\n请使用[.help r]查看掷骰帮助，或使用[.help onedice]查看先进的OneDice标准。",
    "strSetGroupTempRule" : "已设置本群套用模板[{tPcTempName}]的规则[{tPcTempRuleName}]{tLazyResult}",
    "strDelGroupTempRule" : "已清除本群套用模板与规则，将按照人物卡设置各自进行检定",
    "strSetGroupTempError" : "试图套用的模板不存在",
    "strSetGroupTempRuleError" : "试图套用的模板规则不存在",
    "strSetGroupMainDice" : "已设置本群套用主骰[{tResult}]",
    "strShowGroupMainDice" : "本群已套用主骰[{tResult}]",
    "strShowGroupMainDiceNone" : "本群未设置主骰",
    "strDelGroupMainDice" : "已清除本群套用主骰",
    "strSnSet" : "已将[{tUserName}]的群名片修改为[{tResult}]\n若误设置群名片，请使用指令 .st note rm 名片 来清除自定义名片",
    "strSnPcCardNone" : "[{tUserName}]未设置人物卡，无法进行名片设置",
    "strSnSetAtOther" : "已将[{tUserName01}]的群名片修改为[{tResult}]",
    "strSnPcCardNoneAtOther" : "[{tUserName01}]未设置人物卡，无法进行名片设置",
    "strSnAutoOn" : "[{tUserName}]已开启自动群名片功能，人物卡数值变动时将自动更新群名片",
    "strSnAutoAlreadyOn" : "[{tUserName}]的自动群名片功能已处于开启状态",
    "strSnAutoOff" : "[{tUserName}]已关闭自动群名片功能",
    "strSnAutoAlreadyOff" : "[{tUserName}]的自动群名片功能已处于关闭状态",
    "strPcSetMapValueError" : "[{tResult}]不是合法的表达式",
    "strPcInitSet" : "先攻列表已设置:\n{tResult}",
    "strPcInitShow" : "当前先攻列表:\n{tResult}",
    "strPcInitReset" : "重新生成先攻列表:\n{tResult}",
    "strPcInitClear" : "已清空先攻列表",
    "strPcInitShowNode" : "{tId}. [{tSubName}]: {tSubResult}",
    "strPcInitDel" : "已从先攻列表中删除[{tName}]",
    "strPcInit" : "[{tPcTempName}]人物卡作成:{tPcInitResult}",
    "strPcInitErrorRange" : "[{tPcTempName}]人物卡作成失败:\n错误的人物卡作成范围(需为1-10)",
    "strPcUpdateSkillValue" : "[{tName}]的人物卡已更新:\n{tSkillUpdate}",
    "strPcUpdateSkillValueAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]的人物卡更新:\n{tSkillUpdate}",
    "strPcSetSkillValue" : "[{tUserName}]的人物卡[{tName}]已保存",
    "strPcSetSkillValueAtOther" : "[{tUserName01}]的人物卡[{tName}]已保存",
    "strPcSetSpecialSkills" : "\n\n检测到特殊技能{tSpecialSkills}，这些技能会根据相关属性的值进行自动计算。如果手动设置值将覆盖自动计算。若需要自动计算请删除这些技能。",
    "strPcGetSingleSkillValue" : "[{tName}]的[{tSkillName}]: {tSkillValue}",
    "strPcGetSingleSkillValueAtOther" : "[{tUserName}]帮[{tUserName01}]查询人物卡[{tName}]的[{tSkillName}]: {tSkillValue}",
    "strPcGetMultiSkillValue": "[{tName}]的技能属性查询结果如下:\n{tSkillValue}",
    "strPcGetMultiSkillValueAtOther": "[{tUserName}]帮[{tUserName01}]进行的技能属性查询结果如下:\n{tSkillValue}",
    "strPcShow" : "[{tUserName}]的人物卡[{tName}]:\n{tPcShow}",
    "strPcShowAtOther" : "[{tUserName01}]的人物卡[{tName}]:\n{tPcShow}",
    "strPcList" : "[{tName}]的人物卡:\n{tPcList}\n当前选择:{tPcSelection}",
    "strPcLock" : "本群人物卡已锁定(当前人物卡：{tName})，其他群切换人物卡将不影响本群人物卡状态",
    "strPcLockError" : "本群锁定人物卡失败，请重试(当前人物卡：{tName})",
    "strPcLockNone" : "试图锁定的人物卡不存在",
    "strPcUnLock" : "本群人物卡锁定已解除(当前人物卡：{tName})，其他群切换人物卡将同步至本群",
    "strPcUnLockNone" : "本群未启用人物卡锁定功能",
    "strPcInitSt" : "人物卡[{tName}]已按照[{tPcTempName}]完成人物卡作成:{tPcInitResult}",
    "strPcSet" : "人物卡已切换至[{tPcSelection}]",
    "strPcSetError" : "试图切入的人物卡不存在",
    "strPcNew" : "[{tUserName}]的人物卡[{tPcSelection}]已创建",
    "strPcNewAtOther" : "[{tUserName01}]的人物卡[{tPcSelection}]已创建",
    "strPcNewError" : "请附带需要创建的人物卡名称",
    "strPcDel" : "人物卡[{tPcSelection}]已删除",
    "strPcDelError" : "试图删除的人物卡不存在",
    "strPcDelNone" : "人物卡列表为空",
    "strPcClear" : "当前人物卡[{tPcSelection}]已清空",
    "strPcClearNone" : "当前没有人物卡",
    "strPcRm" : "人物卡[{tPcSelection}]的以下{tLenSkillName}条技能已删除: \n{tSkillName}",
    "strPcRmPartialSuccess" : "人物卡[{tPcSelection}]的以下{tLenSkillName}条技能已删除: \n{tSkillName}\n同时以下{tLenFailedSkills}条技能不存在，无法删除: \n{tFailedSkills}",
    "strPcRmNone" : "人物卡[{tPcSelection}]的以下{tLenFailedSkills}条技能不存在，无法删除: \n{tFailedSkills}",
    "strPcRmCardNone" : "人物卡不存在",
    "strPcTemp" : "人物卡[{tPcSelection}]套用模板[{tPcTempName}]",
    "strPcTempShow" : "人物卡[{tPcSelection}]:\n模板[{tPcTempName}]{tResult}",
    "strPcTempError" : "试图套用的模板不存在，或是未设置人物卡",
    "strPcTempRule" : "人物卡[{tPcSelection}]套用模板[{tPcTempName}]的规则[{tPcTempRuleName}]",
    "strPcTempRuleShow" : "人物卡[{tPcSelection}]:\n模板[{tPcTempName}]\n规则[{tPcTempRuleName}]{tResult}",
    "strPcTempRuleError" : "试图套用的模板规则不存在，或是未设置人物卡",
    "strPcGroupTempRuleShow" : "\n\n但本群已全局套用:\n模板[{tPcTempName}]\n规则[{tPcTempRuleName}]",
    "strPcRecRm" : "已删除人物卡[{tName}]的映射[{tSkillName}]",
    "strPcNoteRm" : "已删除人物卡[{tName}]的记录[{tSkillName}]",
    "strPcRecError" : "未找到人物卡[{tName}]对应的映射[{tSkillName}]",
    "strPcNoteError" : "未找到人物卡[{tName}]对应的记录[{tSkillName}]",
    "strPcExportCardNone" : "当前没有人物卡，无法导出",
    "strNoPcInputCard" : "未找到人物卡[{tPcInputCard}]或人物卡[{tPcInputCard}]没有技能数据",
    "strPcCardNoSkill" : "人物卡[{tPcInputCard}]没有可导出的技能",
    "strPcCardExport" : "已成功导出人物卡[{tPcInputCard}]的技能数据：\n{tExport}",
    "strPcBlockRm": "已删除人物卡[{tName}]的[{tBlockName}]技能块内容",
    "strPcBlockRmNone": "人物卡[{tName}]未找到[{tBlockName}]技能块内容",
    "strPcBlockList": "人物卡[{tName}]包含以下技能块:\n{tBlockList}",
    "strPcRename" : "[{tPcSelection}]已重命名为[{tPcSelectionNew}]",
    "strPcSkillCheck" : "[{tName}]进行技能[{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHide" : "于群[{tGroupId}]中[{tName}]进行技能[{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideShow" : "[{tName}]进行技能[{tSkillValue}]暗检定",
    "strPcSkillCheckWithSkillName" : "[{tName}]进行技能[{tSkillName}:{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideWithSkillName" : "于群[{tGroupId}]中[{tName}]进行技能[{tSkillName}:{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideShowWithSkillName" : "[{tName}]进行技能[{tSkillName}:{tSkillValue}]暗检定",
    "strPcSkillCheckAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行技能[{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideAtOther" : "于群[{tGroupId}]中[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行技能[{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideShowAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行技能[{tSkillValue}]暗检定",
    "strPcSkillCheckWithSkillNameAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行技能[{tSkillName}:{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideWithSkillNameAtOther" : "于群[{tGroupId}]中[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行技能[{tSkillName}:{tSkillValue}]检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillCheckHideShowWithSkillNameAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行技能[{tSkillName}:{tSkillValue}]暗检定",
    "strPcSkillEnhanceCheck" : "[{tName}]进行技能[{tSkillName}:{tSkillValue}]成长检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillEnhanceContent" : "\n该技能发生了增长: {tRollSubResult}",
    "strPcSkillEnhanceAll": "[{tName}]的技能成长检定结果:\n技能列表：{tCheckedSkillList}\n共有[{tSkillEnhanceCount}]个技能进行了检定，其中成功[{tSkillEnhanceSucceedCount}]个: {tSkillEnhanceSucceedList}",
    "strPcSkillEnhanceSkipped": "\n跳过成长(特殊属性或0值): {tSkippedSkillList}",
    "strPcSkillEnhanceNotFound": "\n未找到技能: {tNotFoundSkillList}",
    "strPcSkillEnhanceOnlySpecial": "[{tName}]的以下技能均为无法成长的特殊属性或0值技能或未找到对应的技能：\n{tSkippedSkillList}",
    "strPcSkillEnhanceError" : "未设置人物卡，无法进行自动成长检定",
    "strSanCheck" : "[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}点,当前剩余[{tSkillValueNew}]点",
    "strSanCheckGreatFailed" : "[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}的最大值[{tRollSubResultIntMax}]点,当前剩余[{tSkillValueNew}]点",
    "strSanCheckError" : "[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n掷骰表达式[{tRollSubResult}]存在错误",
    "strSanCheckAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}点,当前剩余[{tSkillValueNew}]点",
    "strSanCheckGreatFailedAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}的最大值[{tRollSubResultIntMax}]点,当前剩余[{tSkillValueNew}]点",
    "strSanCheckErrorAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n掷骰表达式[{tRollSubResult}]存在错误",
    "strAtOtherPermissionDenied": "[{tUserName}]不为群主或管理员，没有代骰权限。",
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
    "strPcSkillCheckError" : "发生错误",
    "strRAVShow" : "[{tName}]与[{tName01}]进行技能[{tSkillName}]和技能[{tSkillName01}]的对抗:\n[{tSkillValue} - {tSkillValue01}]\n[{tName}]: {tRollResult} {tSkillCheckReasult}\n[{tName01}]: {tRollResult01} {tSkillCheckReasult01}\n{tRAVResult}",
    "strRAVResult01" : "前者，[{tName}]获胜",
    "strRAVResult02" : "后者，[{tName01}]获胜",
    "strRAVResult03" : "平手",
    "strHelpdocSet" : "自定义帮助文档已设置",
    "strHelpdocDel" : "自定义帮助文档已删除",
    "strObList" : "当前旁观列表:\n{tResult}",
    "strObListNone" : "当前旁观列表为空",
    "strObUserObList" : "当前旁观列表:\n{tResult}",
    "strObUserObListNone" : "当前旁观列表为空",
    "strObJoin" : "[{tUserName}]现已加入旁观",
    "strObJoinAlready" : "[{tUserName}]已在旁观中",
    "strObExit" : "[{tUserName}]现已退出旁观",
    "strObExitAlready" : "[{tUserName}]不在旁观中",
    "strObExitAll" : "[{tUserName}]现已退出所有旁观",
    "strObClear" : "已清空旁观列表",
    "strTeamCreated": "已创建/更新小队[{tTeamName}]，当前成员数: {tMemberCount}\n当前成员列表:\n{tMembers}",
    "strTeamShow": "小队[{tTeamName}]成员列表 ({tMemberCount}人):\n{tMembers}",
    "strTeamList": "当前群组小队列表 ({tTeamCount}个小队):\n{tTeamList}",
    "strMembersRemoved": "已从小队[{tTeamName}]中移除{tRemovedCount}名成员:\n{tRemovedMembers}\n剩余成员数: {tMemberCount}，剩余成员列表:\n{tMembers}",
    "strTeamDeleted": "已删除小队[{tTeamName}]",
    "strTeamCleared": "已清空小队[{tTeamName}]的成员",
    "strTeamAt": "正在通知小队[{tTeamName}]成员:\n{tAtMembers}",
    "strTeamSetActive": "已设置[{tTeamName}]为当前活跃小队",
    "strTeamSortResult": "小队[{tTeamName}]按技能[{tSkillName}]排序结果:\n{tSortResult}",
    "strTeamSortNeedSkill": "请指定要排序的技能名称",
    "strTeamRenamed": "已将小队[{tOldTeamName}]重命名为[{tNewTeamName}]",
    "strTeamRenameNeedNewName": "请指定新的小队名称",
    "strTeamNameExists": "小队名称[{tTeamName}]已存在",
    "strTeamSkillUpdate": "小队[{tTeamName}]的技能更新:\n{tResults}",
    "strTeamCheckResult": "小队[{tTeamName}]进行技能[{tSkillName}]检定:\n{tResult}",
    "strTeamSCResult": "小队[{tTeamName}]进行理智检定:\n{tResult}",
    "strTeamRoll": "小队[{tTeamName}]掷骰:\n{tRollResult}",
    "strTeamRollWithReason": "小队[{tTeamName}]由于[{tReason}]掷骰:\n{tRollResult}",
    "strNoActiveTeam": "当前群组没有活跃小队",
    "strTeamNotFound": "小队[{tTeamName}]不存在",
    "strNoTeams": "当前群组没有创建任何小队",
    "strNoMembersRemoved": "没有移除任何成员",
    "strTeamEmpty": "小队[{tTeamName}]中没有成员"
}
```
