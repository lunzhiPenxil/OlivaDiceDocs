# OlivaDice For OlivOS 骰主手册

*For Ver.3.1.16(1026)*

> *世界是属于每一个人的。要创造一个充满逻辑并尊重每一个人的世界。*    
> *——《Новый Элемент Расселения》A.D.1960 Москва*


> 有关基础搭建的指引请参考[【教程】手把手教你搭建青果骰](https://forum.olivos.run/d/25)

![DIXE(OLIVADICE)](_static/DIXE_OLIVADICE.jpg)

## 插件模块
基于OlivOS的插件机制，新版的青果骰进行了模块化设计，实现了多个插件模块的协同合作，你可以通过安装这些模块来快速的组合功能。  

### OlivaDiceCore | 核心模块
[OlivaDiceCore](https://github.com/OlivOS-Team/OlivaDiceCore)是整个骰子的核心模块，它提供了所有必须的骰子功能以及基础的管理支持，几乎所有的其它模块都依赖这个模块。  

### OlivaDiceJoy | 娱乐模块
[OlivaDiceJoy](https://github.com/OlivOS-Team/OlivaDiceJoy)提供了一些无关紧要的娱乐功能，它们或许是与跑团关系不大、或许只是一些历史原因遗留下来的传统，总之，这些在野蛮生长时期被或是由于开发者无知、或是作为恶性竞争手段、或是用户呼声较大但对于跑团而言意义不明的，被添加进来的小功能，都会被放入这个模块。  

### OlivaDiceLogger | 日志模块
[OlivaDiceLogger](https://github.com/OlivOS-Team/OlivaDiceLogger)提供了跑团日志记录器，它可以在跑团过程中对日志进行记录，并由结果生成跑团日志，与在线的跑团日志渲染器进行联动、或发送日志邮件。  

### OlivaDiceMaster | 大师模块
[OlivaDiceMaster](https://github.com/OlivOS-Team/OlivaDiceMaster)提供了更高级的骰主管理功能，其中的功能可能不是必须的，但是却是强大的，这些功能包括但不限于更新和安装新的模块。  

### OlivaDiceOdyssey | 高阶模块
[OlivaDiceOdyssey](https://github.com/OlivOS-Team/OlivaDiceOdyssey)提供了一些涉及第三方合作的功能，它们或许是调用了第三方数据库，要么是涉及版权授权，又或者是单纯的过于依赖网络，总之这些功能由于第三方的参与很可能无法由插件开发者保证可靠性，但仍然很强大。例如魔都模组功能。  


## 用户策略

### 用户记录
`.uinfo` 查询自己的用户记录  
`.uinfo user` 查询自己的用户记录  
`.uinfo group` 查询本群的群记录  
`.uinfo host` 查询本频道的记录  
`.uinfo user [id]` 查询对应的用户记录  
`.uinfo group [id]` 查询对应的群记录  
`.uinfo host [id]` 查询对应频道的记录  

## 管理指令

### Master绑定/解绑

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

### 通知窗口
`.master notice (del) [群号]`  添加(删除)通知群  

被作为通知窗口的群会在有邀请时受到邀请请求或通知，如果需要手动验证，则会提供相关指令提示  

### 心跳上报
`.master pulse [TOKEN]`  添加心跳TOKEN  
`.master pulse del [URL/TOKEN]`  删除心跳配置  
`.master pulse [URL] [TOKEN]`  添加第三方心跳TOKEN  

更多有关心跳上报的信息请参考[心跳系统](http://benzencloudhk.xyz/dicetoken/)  

### 远程控制
`.master exit [群组ID]`  远程退出特定群  
`.master remote [on/off] [群组ID]`  远程在群中停用  
`.master remote host [on/off] [频道ID]`  远程在频道中停用  
`.master remote host default [on/off] [频道ID]`  远程在频道中默认关闭  

远程控制提供了一种不需要骰主加入相关多人聊天场所即可操作对应场所这些开关的状态的方法  

### 修改配置项
`.master [配置项] [配置值]`  修改配置项  

修改配置项可以更广泛的调整骰子机器人的全局配置  

#### 配置项目表
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

### 远程更新
`.system restart` 重载所有模块  

> 以下功能需要`OlivaDiceMaster 大师模块`

这些指令可以用于远程更新插件  
`.oopm update` 自动检查并更新全部插件  
`.oopm update [插件名称]` 更新特定插件  
`.oopm show [插件名称]` 检查插件更新状态  
`.oopm list` 查看所有可选模块  

## 个性化定制

### 配置文件
骰子可以由一系列配置文件进行直接定制，所有配置文件都在`plugin/data/OlivaDice`路径下，在该路径下会有不同名为账号哈希的目录以及一个`unity`目录，这分别对应每个账号各自的配置以及公用配置，其下配置文件如下，注明默认即为修改、重载时写入、定时刷写、初始化时读取

- OlivaDiceCore 核心模块

| 文件路径                          | 说明                         | 读写时机           |
|:---------------------------------|:----------------------------|:-----------------|
| console/customReply.json         | 自定义回复词                  | 默认              |
| console/switch.json              | 自定义配置项                  | 默认              |
| console/helpdocDefault.json      | 自定义帮助文档                | 默认              |
| extend/deckclassic               | 扩展牌堆                     | 默认              |
| extend/helpdoc                   | 扩展帮助文档                  | 默认              |
| pcCard                           | 自定义配置项                  | 默认              |
| user                             | 用户记录                     | 默认              |

- OlivaDiceLogger 日志模块

| 文件路径                          | 说明                         | 读写时机           |
|:---------------------------------|:----------------------------|:-----------------|
| logger                           | 日志记录文件                  | 默认              |

### 扩展牌堆
扩展牌堆可以扩展`draw`指令可抽取的牌堆种类，扩展牌堆应当放置于`extend/deckclassic`路径下，其本质为格式如下的json文本文件
```json
{
  "!密教模拟器牌堆By仑质":[
    "密教模拟器牌堆By仑质"
  ],
  "密教影响":[
    "推迟行刑\n肉体皆会衰败。但我得到了保证，我的肉体会衰败得稍晚一点。[此卡是在你没有“健康”时对付生病的最后一道保险。]",
    "躁动\n我为一种躁动的向往所俘。我似乎产生了某种……企图。究竟是何企图？",
    "恐惧\n我已经见得太多了。不知名的恐惧正在用利齿啃噬着我的希望；一种关于存在本身的的恐惧。",
    "入迷\n光透过裂缝漏入。我的头脑比任何时候都更清晰。我升得越高，见得越多。",
    "安逸\n我很开心，大概吧。[安逸可以抵御恐惧，但安逸难以久存。]",
    "一瞬追忆\n回首某个瞬间。下个瞬间即告消逝。",
    "活力\n锻炼，或者其他更少见的东西，令我精神振奋。[与另一张“活力”一同使用可提升技能。如果不使用，将会在三分钟后消失。]",
    "活力：学有所成\n我已经准备好改变了。[与“力量”技能一同使用可升级该技能并获得“健康”。五分钟后将会退化回“活力”。]",
    "博闻\n我如饥似渴地吸收着知识，仿佛影子吸收光线。也许我离提升不远了。[研究“博闻”能获得更多“理性”。如果不使用，将会在三分钟后消失。]",
    "博闻：学有所成\n我已经准备好改变了。[与“学识”技能一起使用可提升该技能并获得“理性”。五分钟后会退化回“博闻”。]",
    "灵感\n我的情绪比平常更为高昂。有些事物我永远也不会理解，因而永远都那么珍贵，而如今我离它们更近了一点。[在研究中使用“灵感”可获得“激情”。如果不使用，将会在三分钟后消失。]",
    "灵感：学有所成\n我已经准备好改变了。[与“想象”技能一起使用可升级该技能并获得“激情”。五分钟后将退化回“灵感”。]",
    "名声：秘氛\n离奇之感残留不去。[“秘氛”可能引起猎人注意。猎人没法用它立案调查你，但这会促使他们更努力地寻找证据。]",
    "名声：邪名\n有些行为会长久留存于人们的记忆中。[“邪名”可能使猎人立案调查你。]",
    "证据：不确凿证据\n一名猎人发现了我的罪证——或许为真实，或许为臆造。[拥有密教活动“证据”的猎人会变得更加危险。证据在制作它的猎人死后仍继续存在。]",
    "证据：确凿证据\n“大地啊，开裂吧！哦，不，它不会收容我的。”[掌握密教活动“确凿证据”后，防剿局会以之给你定罪。证据在制作它的猎人死后仍继续存在。]"
  ]
}
```


### 自定义帮助文档
`.helpdoc [帮助名称] [帮助内容]`  设置帮助文档  
`.helpdoc [帮助名称]`  删除帮助文档  

这些指令可以调整帮助文档的词条内容，或是增加新的帮助文档，亦或是删除帮助文档，此外，你还可以通过扩展文件进行扩展。  

#### 扩展帮助文档
扩展帮助文档应当放置于`extend/helpdoc`路径下，其本质为格式如下的json文本文件

```json
{
  "mod":"黑暗之魂查询文档",
  "author":"仑质",
  "brief":"黑暗之魂查询文档",
  "comment":"黑暗之魂查询文档",
  "helpdoc":{
    "ds":"黑暗之魂查询文档\n包含黑暗之魂三部曲中的武器、装备、道具、戒指、法术、生物\n全部文案来自黑暗之魂游戏数据解包，版权归FromSoftware所有。\n作者：仑质\n\n查询指令：.help ds[1/2/3] [所查词条] [序号]\n序号项通常不需要，在需要时将会提示。",
    "ds1 白标记蜡石":"白标记蜡石\n效果：书写召唤记号\n联机游玩专用道具，能书写召唤记号。\n\n可从记号处受召前往其他世界，并以灵体姿态行动，\n只要成功打倒受召前往区域的主人，就能获得人性。\n（游魂状态时无法使用召唤。）\n\n这是在时间停滞不动的罗德兰一地，\n不死人照应彼此的手段。",
    "ds1 红标记蜡石":"红标记蜡石\n效果：书写侵入记号\n联机游玩专用道具，能书写侵入记号。\n（游魂状态时无法使用。）\n\n可从记号处受召前往其他世界，并以暗灵姿态行动，\n成功打倒召唤者，就可以获得人性。\n\n在化为吸魂鬼，堕入黑暗的人之中，\n也有无法抛下身为人的荣耀，以及骑士道的人，\n这正是为了他们所准备的手段。",
    "ds1 血红眼眸宝珠":"血红眼眸宝珠\n效果：侵入其他世界\n联机游玩专用道具，能侵入其他世界。\n（订立誓约者才可使用，游魂状态无法使用。）\n\n只要在侵入的世界中，\n打倒该世界的主人，就能获得人性。\n\n此乃遭到卡斯唆使的吸魂鬼之常见行径，\n他们越是追求人性，越会堕入更深层的黑暗。\n或许该说，这才是人类真正会有的作为呢？",
    "ds1 诀别黑水晶":"诀别黑水晶\n效果：使灵体回到原来的世界、从其他世界回到原来的世界\n成为不死人的放逐者所拿到的黑水晶，\n自古以来就代表着诀别。\n召唤者可借此让召唤出的灵体回到原来的世界，\n灵体则能借此从其他世界回到原来的世界。\n\n但若珍惜人与人的缘分，\n就不该轻率地使用这项道具。",
    "ds1 橘建言蜡石":"橘建言蜡石\n效果：书写、确认、评价讯息\n联机游玩专用道具，\n能够书写、确认、评价讯息。\n\n写出的讯息将被送往其他世界，并受他人评价，\n也可以评价来自其他世界的讯息。\n\n这是在时间停滞不动的罗德兰一地，\n不死人照应彼此的手段，\n同时，也是种互相欺骗的手段。",
    "ds1 罪人录":"罪人录\n效果：确认世界的罪人名单\n联机游玩专用道具，\n能够确认世界的罪人名单。\n\n此为罪业女神蓓尔嘉管理的纪录本。\n所谓的罪人，便是那些藐视诸神与誓约之人，\n他们无法逃过遭暗月之刃制裁的命运。",
    "ds1 死者眼眸":"死者眼眸\n效果：将灵体从其他世界引诱过来\n联机游玩专用道具，能够将灵体从其他世界引诱过来。\n（订立誓约者才可使用，游魂状态无法使用。）\n\n带有祸患气息的“死者眼眸”可以对其他世界散播灾厄，\n是种将其他灵体化为牺牲者，引诱至自身世界的手段。\n而牺牲者也会产生“死者眼眸，”使得灾厄更加扩散。",
    "ds1 龟裂血红眼眸宝珠":"龟裂血红眼眸宝珠\n效果：侵入其他世界\n联机游玩专用道具，能侵入其他世界。\n（游魂状态无法使用。）\n\n只要在侵入的世界中，\n打倒该世界的主人，就能获得人性。\n\n此乃遭到卡斯唆使的吸魂鬼之常见行径，\n可以借由这已经裂开的红色宝珠，\n暂时模仿他们的所作所为。"
    }
}
```


### 自定义回复词
`.str[配置项] [配置值]`  修改对应的自定义配置  
`.str[配置项]`  查看对应的自定义配置  

本核心内置了一套str回复词配置工具，可以通过以上指令进行骰子回复词的配置，例如：  
使用  
`[.strPcSkillCheckFailed 哈哈，失败，哈哈]`  
即可将检定失败回复词进行设置。  

需要特别指出的是，`.help`指令回复的内容不属于自定义回复的范畴，而是属于自定义帮助文档，其内容与`help default`一致，可以通过`helpdoc`指令进行设置  

#### 自定义回复表
以下为可以用于`console/customReply.json`文件的内容，其键值对关系也可以用于上文所提到的`str`指令设置  

- OlivaDiceCore 核心模块
```json
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
```json
{
    "strJoyJrrp": "[{tName}]的今日人品为[{tJrrpResult}]",
    "strJoyZrrp": "[{tName}]的昨日人品为[{tJrrpResult}]",
    "strJoyMrrp": "[{tName}]的明日人品为[{tJrrpResult}]"
}
```

- OlivaDiceLogger 日志模块
```json
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
```json
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
```json
{
    "strOdysseyCnmodsSearch": "魔都模组搜索结果如下:\n{tCnmodsResult}",
    "strOdysseyCnmodsLuck": "魔都模组推荐如下:\n{tCnmodsResult}"
}
```


