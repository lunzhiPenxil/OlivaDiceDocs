# OlivaDice For OlivOS 骰主手册

*For Ver.3.1.16(1026)*

> *世界是属于每一个人的。要创造一个充满逻辑并尊重每一个人的世界。*    
> *——《Новый Элемент Расселения》A.D.1960 Москва*

> 有关基础搭建的指引请参考[【教程】手把手教你搭建青果骰](https://forum.olivos.run/d/25)

![DIXE(OLIVADICE)](_static/DIXE_OLIVADICE.jpg)

### 管理指令

#### Master绑定/解绑

Master是骰子的控制者，每个骰娘同时可以有多个Master。Master可以控制骰子的发言和行为，并个性化大量配置。
在插件启动时将会显示有关骰子认主指令的具体提示，每完成一次认主，口令将会刷新。  
形如：  
```
[2022-05-13 15:58:30] - [INFO] - [OlivaDice] - [Init] - [185]条[人物卡]数据已加载
[2022-05-13 15:58:32] - [INFO] - [OlivaDice] - [Init] - [972]条[用户记录]数据已加载
[2022-05-13 15:58:32] - [INFO] - [OlivaDice] - [Init] - 请使用[.master 87207e9d-fe0e-4613-92a6-da8df350748a]指令以获取Master权限
[2022-05-13 15:58:32] - [INFO] - [OlivaDice] - [Init] - 当前版本为[3.1.16(1026)]
```

完成认主后将会有明确提示  
`.master [验证口令]`  骰子认主  
`.master master (del) [ID]`  添加(删除)骰主  

#### 通知窗口
`.master notice (del) [群号]`  添加(删除)通知群  

#### 心跳上报
`.master pulse [TOKEN]`  添加心跳TOKEN  
`.master pulse del [URL/TOKEN]`  删除心跳配置  
`.master pulse [URL] [TOKEN]`  添加第三方心跳TOKEN  

#### 远程控制
`.master remote [on/off] [群组ID]`  远程在群中停用  
`.master remote host [on/off] [频道ID]`  远程在频道中停用  
`.master remote host default [on/off] [频道ID]`  远程在频道中默认关闭  

#### 修改配置项
`.master [配置项] [配置值]`  修改配置项  

##### 配置项目表
- OlivaDiceCore 核心模块

| 关键词                   |  默认状态  | 说明                                              |
|:------------------------|:--------:|:--------------------------------------------------|
| BelieveOlivaDicelist    | 0        | 控制是否拉取OlivaDicelist                           |
| autoAcceptFriendAdd     | 1        | 自动同意好友添加请求                                 |
| autoAcceptGroupAdd      | 1        | 自动同意群邀请                                      |
| messageFliterMode       | 0        | 事件过滤器<br/>`1`时屏蔽普通群消息<br/>`2`时屏蔽频道消息<br/>`3`时屏蔽所有多人窗口消息 |
| disableReplyPrivate     | 0        | 禁用私聊                                           |
| pulseInterval           | 300      | 心跳上报频率，通常不需要调整                           |
| userConfigCount         | 100      | 用户记录刷写循环计数器，通常不需要调整                   |
| globalEnable            | 1        | 当前版本无用，通常不需要调整                           |

- OlivaDiceJoy 娱乐模块

| 关键词                   |  默认状态  | 说明                                              |
|:------------------------|:--------:|:--------------------------------------------------|
| joyPokeMode             | 0        | 控制戳一戳的返回内容<br/>`0`返回默认版本号<br/>`1`进行一次`1D100`掷骰 |

### 用户策略

#### 用户记录
`.uinfo` 查询自己的用户记录  
`.uinfo user` 查询自己的用户记录  
`.uinfo group` 查询本群的群记录  
`.uinfo host` 查询本频道的记录  
`.uinfo user [id]` 查询对应的用户记录  
`.uinfo group [id]` 查询对应的群记录  
`.uinfo host [id]` 查询对应频道的记录  

### 个性化定制

#### 自定义帮助文档
`.helpdoc [帮助名称] [帮助内容]`  设置帮助文档  
`.helpdoc [帮助名称]`  删除帮助文档  

#### 自定义回复词
`.str[配置项] [配置值]`  修改对应的自定义配置  
`.str[配置项]`  查看对应的自定义配置  

本核心内置了一套str回复词配置工具，可以通过以上指令进行骰子回复词的配置，例如：  
使用  
`[.strPcSkillCheckFailed 哈哈，失败，哈哈]`  
即可将检定失败回复词进行设置。  

需要特别指出的是，`.help`指令回复的内容不属于自定义回复的范畴，而是属于自定义帮助文档，其内容与`help default`一致，可以通过`helpdoc`指令进行设置  

##### 自定义回复表
- OlivaDiceCore 核心模块
```python
{
    "strBotName": "Bot",
    "strForGroupOnly": "此功能仅对群聊开放",
    "strSetStr": "回复词[{tStrName}]已更新",
    "strBecomeMaster": "口令正确，[{tName}]已成为Master",
    "strCantBecomeMaster": "无Master权限且口令错误，拒绝认证",
    "strMasterSystemRestart": "[{tName}]远程调用重载",
    "strMasterConsoleShow": "[{tConsoleKey}]当前为[{tConsoleValue}]",
    "strMasterConsoleShowList": "[{tConsoleKey}]当前为:\n{tConsoleValue}",
    "strMasterConsoleSet": "[{tName}]已将[{tConsoleKey}]设置为[{tConsoleValue}]",
    "strMasterConsoleAppend": "[{tName}]已修改[{tConsoleKey}]条目",
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
    "strRollError11" : "表达式[{tRollPara}]掷骰错误！解析技能变量时出错！",
    "strRollErrorUnknown" : "表达式[{tRollPara}]掷骰错误！未知的错误: {tResult}",
    "strRollErrorHelp" : "\n请使用[.help r]查看掷骰帮助，或使用[.help onedice]查看先进的OneDice标准。",
    "strSetGroupTempRule" : "已设置本群套用模板[{tPcTempName}]的规则[{tPcTempRuleName}]{tLazyResult}",
    "strDelGroupTempRule" : "已清除本群套用模板与规则，将按照人物卡设置各自进行检定",
    "strPcInit" : "[{tPcTempName}]人物卡作成:{tPcInitResult}",
    "strPcUpdateSkillValue" : "[{tName}]的人物卡已更新:\n[{tSkillName}]: {tSkillUpdate}",
    "strPcSetSkillValue" : "[{tName}]的人物卡已保存",
    "strPcGetSingleSkillValue" : "[{tName}]的[{tSkillName}]: {tSkillValue}",
    "strPcShow" : "人物卡[{tName}]:\n{tPcShow}",
    "strPcList" : "[{tName}]的人物卡:\n{tPcList}\n当前选择:{tPcSelection}",
    "strPcInitSt" : "人物卡[{tName}]已按照[{tPcTempName}]完成人物卡作成:{tPcInitResult}",
    "strPcSet" : "人物卡已切换至[{tPcSelection}]",
    "strPcSetError" : "试图切入的人物卡不存在",
    "strPcDel" : "人物卡[{tPcSelection}]已删除",
    "strPcDelError" : "试图删除的人物卡不存在",
    "strPcDelNone" : "人物卡列表为空",
    "strPcClear" : "当前人物卡[{tPcSelection}]已清空",
    "strPcClearNone" : "当前没有人物卡",
    "strPcRm" : "人物卡[{tPcSelection}]的[{tSkillName}]已删除",
    "strPcRmNone" : "人物卡[{tPcSelection}]的[{tSkillName}]不存在",
    "strPcRmCardNone" : "人物卡不存在",
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
    "strPcSkillEnhanceCheck" : "[{tName}]进行技能[{tSkillName}:{tSkillValue}]成长检定: {tRollResult} {tSkillCheckReasult}",
    "strPcSkillEnhanceContent" : "\n该技能发生了增长: {tRollSubResult}",
    "strPcSkillEnhanceAll" : "[{tName}]进行技能自动成长检定:\n共有[{tSkillEnhanceCount}]个技能进行了检定，其中成功[{tSkillEnhanceSucceedCount}]个: {tSkillEnhanceSucceedList}",
    "strPcSkillEnhanceError" : "未设置人物卡，无法进行自动成长检定",
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
    "strPcSkillCheckError" : "发生错误",
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
    "strObClear" : "已清空旁观列表"
}
```

- OlivaDiceJoy 娱乐模块
```python
{
    "strJoyJrrp": "[{tName}]的今日人品为[{tJrrpResult}]",
    "strJoyZrrp": "[{tName}]的昨日人品为[{tJrrpResult}]",
    "strJoyMrrp": "[{tName}]的明日人品为[{tJrrpResult}]"
}
```

- OlivaDiceLogger 日志模块
```python
{
    "strLoggerLogOn": "开始记录日志",
    "strLoggerLogAlreadyOn": "已经正在记录日志",
    "strLoggerLogContinue": "继续记录日志",
    "strLoggerLogOff": "暂停记录日志",
    "strLoggerLogAlreadyOff": "没有正在进行的日志",
    "strLoggerLogEnd": "停止记录日志",
    "strLoggerLogAlreadyEnd": "没有正在进行的日志",
    "strLoggerLogSave": "日志[{tLogName}]已保存",
    "strLoggerLogUrl": "日志已上传，请在[{tLogUrl}]提取日志"
}
```

- OlivaDiceMaster 大师模块
```python
{
    "strMasterReply": "{tMasterResult}",
    "strMasterOopmApiFailed": "更新源访问失败",
    "strMasterOopmNotMatch": "未找到匹配模块条目",
    "strMasterOopmDownload": "{tMasterOopkNameList}\n模块已下载成功",
    "strMasterOopmCopy": "{tMasterOopkNameList}\n模块已安装成功",
    "strMasterOopmUpdate": "{tMasterOopkNameList}\n模块已更新成功",
    "strMasterOopmUpdateAllDone": "所选模块已更新成功，即将重载",
    "strMasterOopmUpdateNotNeed": "所有模块已为最新版本，无需更新",
    "strMasterOopmUpdateNotSkipSrc": "{tMasterOopkNameList}\n模块为手动部署模式，已跳过",
    "strMasterOopmUpdateNotSkipDev": "{tMasterOopkNameList}\n模块为开发模式，已跳过",
    "strMasterOopmDownloadFailed": "{tMasterOopkNameList}\n模块下载失败",
    "strMasterOopmCopyFailed": "{tMasterOopkNameList}\n模块安装失败"
}
```

- OlivaDiceOdyssey 高阶模块
```python
{
    "strOdysseyCnmodsSearch": "魔都模组搜索结果如下:\n{tCnmodsResult}",
    "strOdysseyCnmodsLuck": "魔都模组推荐如下:\n{tCnmodsResult}"
}
```


