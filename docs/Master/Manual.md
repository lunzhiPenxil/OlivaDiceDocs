# OlivaDice For OlivOS 骰主手册

*For Ver.3.4.45(1125)*

> *世界是属于每一个人的。要创造一个充满逻辑并尊重每一个人的世界。*    
> *——《[Новый Элемент Расселения](https://ru.wikipedia.org/wiki/%D0%9D%D0%BE%D0%B2%D1%8B%D0%B9_%D1%8D%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82_%D1%80%D0%B0%D1%81%D1%81%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F)》A.D.1960 Москва*


> 有关基础搭建的指引请参考[【教程】手把手教你搭建青果骰](https://forum.olivos.run/d/25)

![DIXE(OLIVADICE)](/_static/DIXE_OLIVADICE.jpg)

## 前言
“骰子机器人”的本质，是一个通过或非官方（QQ）协议以及工具，或官方（Telegram、开黑啦等）开放平台接口，实现的一个部分或者全部由骰子机器人软件及其控制的普通用户账号或特殊账号的集合体，而“骰子”一词则，将该集合体的目标功能，限定为服务发生于这些场景的跑团中，提供模拟掷骰的功能以及其他与跑团相关的功能。  
所以，将跑团骰子机器人与娱乐机器人等同的观点是完全错误的，如果出现了这类混淆视听的观点，请确认他们所说的是不是“骰娘”这类意义更加丰富的词，而非“骰子”。  

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

### OlivaDiceNativeGUI | 设置面板
[OlivaDiceNativeGUI](https://github.com/OlivOS-Team/OlivaDiceNativeGUI)提供了传统UI模块，可以对骰子进行简单的可视化设置。  

### ChanceCustom | 程心自定义
[ChanceCustom](https://github.com/OlivOS-Team/ChanceCustom)此插件为`酷Q(CoolQ)`时代的知名插件`铃心自定义(club.myepk.customReply)`的OlivOS版本，采用Python重构，可独立于青果核心基于OlivOS运行，但也可以进行一定程度的双向联动，通常来说可用于对骰子功能的扩展。  


## 特别事项
对于当前版本的`OlivOS`，当在`Windows`操作系统上运行`QQ`平台的机器人时，会在`gocqhttp终端`中出现提示  
> [2022-10-13 16:55:18] [WARNING]: 上报 Event 数据 ... 失败: Post “http://127.0.0.1:55001/OlivOSMsgApi/qq/onebot/gocqhttp”: context deadline exceeded (Client.Timeout exceeded while awaiting headers)

这类警告是由于`Windows`与`GNU`通用范式在中文编码上不兼容，需要你将`计算机全名`修改为纯英文，在某些厂商的笔记本电脑中，该设置默认带有中文（例如小米笔记本）。  

对于`Windows11`，修改流程为：`右键 此电脑（我的电脑）` -> `选择 属性` -> `选择 高级系统设置` -> `选择 计算机名` -> `点击 “要重命名这台计算机... 旁的 更改”`  


## 图形设置面板

> 以下功能需要`OlivaDiceNativeGUI 设置面板`  

(https://github.com/OlivOS-Team/OlivaDiceNativeGUI)提供了传统UI模块，可以对骰子进行简单的可视化设置。  

你可以在任务栏右下角托盘区域，找到OlivOS的图标，`右键`打开菜单后 `插件菜单 > OlivaDice设置面板 > 打开设置`，来打开这个图形设置面板。  

## 用户策略

### 用户记录
`.uinfo` 查询自己的用户记录  
`.uinfo user` 查询自己的用户记录  
`.uinfo group` 查询本群的群记录  
`.uinfo host` 查询本频道的记录  
`.uinfo user [id]` 查询对应的用户记录  
`.uinfo group [id]` 查询对应的群记录  
`.uinfo host [id]` 查询对应频道的记录  

> 以下功能需要`OlivaDiceMaster 大师模块`  

`.trust [user/group/host] [id]` 对某个[用户/多人聊天/频道]设置信任等级  
`.trustlevel [user/group/host] [id]` 对某个[用户/多人聊天/频道]设置信任等级  
`.trustrank [user/group/host] [id]` 对某个[用户/多人聊天/频道]设置信任评分  

> 需要注意，当前将信任等级设置为`0`时，将不会被信任。  
需要注意，当前将信任等级设置为`>=2`时，将会被信任为白名单。  

## 管理指令

### Master绑定/解绑

Master是骰子的控制者，每个骰娘同时可以有多个Master。Master可以控制骰子的发言和行为，并个性化大量配置。
在插件启动时将会显示有关骰子认主指令的具体提示，**或是在设置面板首页可以找到复制指令的按钮**，每完成一次认主，口令将会刷新。  
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

#### KOOK机器人开放市场心跳上报
如果你知道这是什么的话，你应当能在后台获得一个可以被刷新的`UUID`  
你需要将它填写至`strOdysseyKOOKBotMarketPulseUUID`的自定义文本中  
此外，你还需要将`odysseyKOOKBotMarketPulseEnable`配置项置为`1`  
如果你在日志中看到了`KOOK机器人服务平台心跳上报成功！`的字样，则说明你设置成功了  

### 远程控制
`.master exit [群组ID]`  远程退出特定群  
`.master remote [on/off] [群组ID]`  远程在群中停用  
`.master remote host [on/off] [频道ID]`  远程在频道中停用  
`.master remote host default [on/off] [频道ID]`  远程在频道中默认关闭  

远程控制提供了一种不需要骰主加入相关多人聊天场所即可操作对应场所这些开关的状态的方法  

> 以下功能需要`OlivaDiceMaster 大师模块`  

`.group clear [天数]` 查找超过对应天数未触发的多人聊天  
`.group clear do [天数]` 清理超过对应天数未触发的多人聊天  

> 需要注意，加入白名单的群将不会被该指令清除。  


### 修改配置项
`.master [配置项] [配置值]`  修改配置项  

修改配置项可以更广泛的调整骰子机器人的全局配置  

#### 配置项目表
- OlivaDiceCore 核心模块

| 关键词                   |  默认状态  | 说明                                              |
|:------------------------|:--------:|:--------------------------------------------------|
| autoAcceptFriendAdd     | 1        | 自动同意好友添加请求                                 |
| autoAcceptGroupAdd      | 1        | 自动同意群邀请                                      |
| messageFliterMode       | 0        | 事件过滤器<br/>`1`时屏蔽普通群消息<br/>`2`时屏蔽频道消息<br/>`3`时屏蔽所有多人窗口消息 |
| disableReplyPrivate     | 0        | 禁用 rh 等功能 Bot 向用户主动私聊          |
| disablePrivate          | 0        | 禁用私聊                                           |
| pulseInterval           | 300      | 心跳上报频率，通常不需要调整                           |
| userConfigCount         | 100      | 用户记录刷写循环计数器，通常不需要调整                   |
| globalEnable            | 1        | 当前版本无用，通常不需要调整                           |
| messageSplitGate        | 650      | 分页门限，超过此长度的文本将被分页处理                   |
| messageSplitPageLimit   | 10       | 分页上限，超过此数量的页面将不再被发送                   |
| messageSplitDelay       | 1000     | 分页延迟，每个分页间将会等待如此长时间再次发送，单位为毫秒   |
| largeRollLimit          | 300      | 大型掷骰细节长度限制<br/>用于控制诸如ww和dx指令的细节显示<br/>超过将不显示细节 |
| randomMode              | 0        | 随机数生成模式<br/> `0` 默认的尽量使用真随机数<br/> `1` 强制使用本地生成的伪随机数 |
| drawRecommendMode       | 1        | 牌堆抽取推荐模式<br/> `0` 关闭模糊匹配推荐<br/> `1` 开启常规模糊匹配推荐 |
| drawListMode            | 2        | 牌堆帮助文档模式<br/> `0` 关闭自动生成牌堆帮助文档<br/> `1` 生成传统模式的牌堆帮助文档<br/> `2` 生成新版的牌堆帮助文档<br/> `3` 生成新版紧凑的牌堆帮助文档 |
| recordBotJoinGroup      | 1        | 记录Bot加入群组的信息<br/>`0`关闭<br/>`1`开启 |
| multiRollDetail         | 1        | 多次掷骰细节显示模式<br/>`0`不显示细节<br/>`1`显示每次掷骰的细节(默认) |
| helpRecommendGate       | 25       | 帮助文档模糊搜索条目上限<br/>只有小于这个上限的条目可以被推荐<br/>默认为25 |
| censorMode              | 1        | 敏感词审查模式<br/>`0`关闭敏感词审查<br/>`1`启用敏感词审查 |
| censorMatchMode         | 1        | 敏感词审查匹配模式<br/>`0`短词条优先<br/>`1`长词条优先 |
| defaultShowDefault      | 0        | 默认显示默认值<br/>`0`显示所有技能<br/>`1`只显示非默认值技能 |
| defaultAutoSn           | 0        | 默认自动更新群名片<br/>`0`关闭<br/>`1`开启 |

- OlivaDiceLogger 日志模块

| 关键词                   |  默认状态  | 说明                                              |
|:------------------------|:--------:|:--------------------------------------------------|
| defaultLogQuote         | 0        | 是否默认开启日志自动引用上次记录，默认关闭<br/>`0`关闭<br/>`1`开启<br/>新群将默认使用此设置 |
| defaultLogUsePcName     | 0        | 是否默认开启日志使用角色卡名字，默认关闭<br/>`0`关闭<br/>`1`开启<br/>新群将默认使用此设置<br/>开启后日志记录时将使用发送者的角色卡名字 |
| defaultLogUploadTimeout | 60       | 日志上传超时时间（秒），默认60秒<br/>当网络较差时，日志上传可能会超时<br/>超时后将自动保存日志并解锁，用户可稍后使用 `.log upload` 手动上传<br/>建议范围: 30-120秒 |

- OlivaDiceJoy 娱乐模块

| 关键词                   |  默认状态  | 说明                                              |
|:------------------------|:--------:|:--------------------------------------------------|
| joyPokeMode             | 0        | 控制戳一戳的返回内容<br/>`0`返回默认版本号<br/>`1`进行一次默认骰掷骰<br/>`2`进行一次今日人品查询<br/>`3`关闭 |
| joyEnableCCPK           | 0        | 是否对回复词启用程心自定义解析<br/>`0`默认原版<br/>`1`开启程心自定义解析 |
| differentJrrpMode       | 0        | 是否启用不同用户在不同的 Bot 中今日人品结果不同，默认关闭<br/>`0`关闭<br/>`1`开启 |

- OlivaDiceMaster 大师模块

| 关键词                   |  默认状态  | 说明                                              |
|:------------------------|:--------:|:--------------------------------------------------|
| masterAutoUpdate        | 1        | 是否进行自动更新<br/>`0`关闭自动更新<br/>`1`开启自动更新 |

- OlivaDiceOdyssey 高阶模块

| 关键词                   |  默认状态  | 说明                                              |
|:------------------------|:--------:|:--------------------------------------------------|
| odysseyRulesItemLimit          | 8        | 规则速查单页显示条目数量上限 |
| odysseyKOOKBotMarketPulseEnable | 0       | KOOK机器人开放市场心跳上报开关<br/>`0`关闭<br/>`1`开启 |
| odysseyKOOKPlayGameMode        | 1        | KOOK平台在玩游戏/听音乐模式<br/>0 关闭<br/>1 正在玩 青果核心OlivaDice<br/>2 正在听音乐 歌名、歌手可用对应str设置<br/>3 正在玩游戏 游戏ID可用对应str设置 |
| odysseyKOOKPlayGameMusicSoftware | 0      | KOOK平台在玩听音乐的平台, 默认网易云<br/>0 网易云<br/>1 QQ音乐<br/>2 酷狗音乐 |

### 远程更新
`.system restart` 重载所有模块  

> 以下功能需要`OlivaDiceMaster 大师模块`  

这些指令可以用于远程更新插件  
`.oopm update` 自动检查并更新全部插件  
`.oopm update [插件名称]` 更新特定插件  
`.oopm show [插件名称]` 检查插件更新状态  
`.oopm list` 查看所有可选模块  
`.oopm get [插件名称]` 获取对应的可选模块  

### 自动更新
> 以下功能需要`OlivaDiceMaster 大师模块`  

骰子会在初始化之后每隔1小时检查一次版本，并自动更新找到更新内容的模块。  
`.master masterAutoUpdate 0`  关闭自动更新  
`.master masterAutoUpdate 1`  开启自动更新  

### 反馈发送

> 以下功能需要`OlivaDiceMaster 大师模块`  

- 对于普通用户  
`.send [反馈消息]` 发送反馈消息给Master  

- 对于骰主  
`.send [回复消息]` 发送消息到当前窗口  
`.send (user/group) [ID] [回复消息]` 发送消息到指定窗口  

### 数据备份

> 以下功能需要`OlivaDiceMaster 大师模块`

骰子支持定时自动备份和手动备份数据，备份文件保存在`./plugin/backup`目录下。  

`.backup` 查看备份配置和状态  
`.backup start` 手动触发数据备份  
`.backup change 配置项 配置值` 修改备份配置  
`.backup 配置项` 查看指定配置项的值  

#### 可用配置项及默认值
| 配置项 | 默认值 | 说明 |
|:------|:------|:-----|
| isBackup | 0 | 自动备份开关 (0=开启, 1=关闭) |
| startDate | 当前日期 | 备份开始日期 (yyyy-MM-dd格式) |
| passDay | 1 | 备份间隔天数 (整数，每隔几天备份一次) |
| backupTime | 04:00:00 | 自动备份时间 (HH:mm:ss格式) |
| maxBackupCount | 1 | 最大备份数量 (整数，超过将自动删除旧备份) |

备份文件格式为：`data_yyyy-MM-dd_HH-mm-ss.zip`

> 示例：
> `.backup change startDate 2024-01-01` 设置备份开始日期
> `.backup change passDay 7` 设置每7天备份一次
> `.backup change backupTime 03:00:00` 设置凌晨3点进行备份
> `.backup change maxBackupCount 5` 设置最多保留5个备份文件

### 多账号连接管理

> 以下功能需要`OlivaDiceMaster 大师模块`  

骰子支持多账号间建立主从关系，从账号可以使用主账号的数据。这在需要切换账号或导入数据时非常有用。  

`.account link [从账号Hash] [主账号Hash]` 建立主从关系  
`.account unlink [从账号Hash]` 断开主从关系  
`.account list` 列出所有账号和主从关系  
`.account show (账号Hash)` 显示账号详细信息  
`.account import path [路径] (源账号Hash)` 从压缩包导入账号数据  
`.account import hash [源账号Hash]` 从指定账号导入数据  
`.account export (账号Hash)` 导出账号数据  

#### 功能说明
- **建立主从关系**：从账号和主账号可用空格、分号、逗号分隔，系统会自动检测循环依赖并阻止  
- **断开主从关系**：断开后，从账号将恢复为独立账号  
- **列出账号**：显示所有账号的Hash和对应的主从关系状态  
- **显示账号信息**：不指定Hash时显示当前账号，否则查询指定账号的连接状态和数据重定向状态  
- **导入数据**：  
 - 从压缩包导入：路径和源账号Hash可用空格、分号、逗号分隔，源账号Hash可选，如未提供则尝试从文件名自动识别  
 - 从指定账号导入：将源账号的数据复制到当前账号  
 - 操作前会自动备份目标账号数据  
- **导出数据**：不指定Hash时导出当前账号数据，否则导出指定账号的数据到压缩包（默认路径：`./plugin/export`）  

> 示例：  
> `.account link abc123 def456` 将abc123设为从账号，def456设为主账号  
> `.account show` 查看当前账号的连接状态  
> `.account export` 导出当前账号数据  


## 个性化定制

### 配置文件
骰子可以由一系列配置文件进行直接定制，所有配置文件都在`plugin/data/OlivaDice`路径下，在该路径下会有不同名为账号哈希的目录以及一个`unity`目录，这分别对应每个账号各自的配置以及公用配置，其下配置文件如下，注明默认即为修改、重载时写入、定时刷写、初始化时读取

- OlivaDiceCore 核心模块

| 文件路径                          | 说明                         | 读写时机           |
|:---------------------------------|:----------------------------|:-----------------|
| console/customReply.json         | 自定义回复词                  | 默认              |
| console/switch.json              | 自定义配置项                  | 默认              |
| console/helpdocDefault.json      | 自定义帮助文档                | 默认              |
| extend/deckclassic               | json扩展牌堆                 | 加载时只读         |
| extend/deckyaml                  | yaml扩展牌堆                 | 加载时只读         |
| extend/deckexcel                 | excel扩展牌堆                | 加载时只读         |
| extend/helpdoc                   | 扩展帮助文档                  | 加载时只读         |
| extend/template                  | 扩展人物卡模板                | 加载时只读         |
| pcCard                           | 自定义配置项                  | 默认              |
| user                             | 用户记录                     | 默认              |

- OlivaDiceLogger 日志模块

| 文件路径                          | 说明                         | 读写时机           |
|:---------------------------------|:----------------------------|:-----------------|
| logger                           | 日志记录文件                  | 默认              |

### 扩展牌堆
扩展牌堆可以扩展`draw`指令可抽取的牌堆种类，目前支持：  
+ json  青果/溯洄系牌堆  
+ yaml  塔系牌堆  
+ excel 梨系牌堆  

#### json 青果/溯洄系牌堆
扩展牌堆应当放置于`extend/deckclassic`路径下，其本质为格式如下的json文本文件  

??? json青果溯洄系牌堆
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

#### yaml 塔系牌堆
扩展牌堆应当放置于`extend/deckyaml`路径下，其本质为格式如下的yaml文本文件  

由于`yaml`牌堆实际上具有二级结构：  

 - 如下`密教影响`牌堆，需要以`.draw 密教 密教影响`或`.draw 密教:密教影响`来抽取牌堆  
 - 如下`default`牌堆，需要以`.draw 密教`或`.draw 密教 default`或`.draw 密教:default`来抽取牌堆  

??? yaml塔系牌堆
    ```yaml
    #必要信息
    name: 密教
    author: 仑质
    version: 200323
    command: 密教
    desc: 密教模拟器卡牌抽取
    includes:
      - "default"
      - "密教影响"

    #作者信息
    info:
      - "本牌堆使用Json2Yaml(By BenzenPenxil)自动转换生成\n转换器版本号：1.0.8.20200122.1\n牌堆原作者：仑质\n全部文案来自密教模拟器wiki，版权归WeatherFactory所有。"

    #牌堆部分
    default:
      - "影响|{%密教影响}"

    密教:
      - "影响|{%密教影响}"

    密教影响:
      - "推迟行刑\n肉体皆会衰败。但我得到了保证，我的肉体会衰败得稍晚一点。[此卡是在你没有“健康”时对付生病的最后一道保险。]",
      - "躁动\n我为一种躁动的向往所俘。我似乎产生了某种……企图。究竟是何企图？",
      - "恐惧\n我已经见得太多了。不知名的恐惧正在用利齿啃噬着我的希望；一种关于存在本身的的恐惧。",
      - "入迷\n光透过裂缝漏入。我的头脑比任何时候都更清晰。我升得越高，见得越多。",
      - "安逸\n我很开心，大概吧。[安逸可以抵御恐惧，但安逸难以久存。]",
      - "一瞬追忆\n回首某个瞬间。下个瞬间即告消逝。",
      - "活力\n锻炼，或者其他更少见的东西，令我精神振奋。[与另一张“活力”一同使用可提升技能。如果不使用，将会在三分钟后消失。]",
      - "活力：学有所成\n我已经准备好改变了。[与“力量”技能一同使用可升级该技能并获得“健康”。五分钟后将会退化回“活力”。]",
      - "博闻\n我如饥似渴地吸收着知识，仿佛影子吸收光线。也许我离提升不远了。[研究“博闻”能获得更多“理性”。如果不使用，将会在三分钟后消失。]",
      - "博闻：学有所成\n我已经准备好改变了。[与“学识”技能一起使用可提升该技能并获得“理性”。五分钟后会退化回“博闻”。]",
      - "灵感\n我的情绪比平常更为高昂。有些事物我永远也不会理解，因而永远都那么珍贵，而如今我离它们更近了一点。[在研究中使用“灵感”可获得“激情”。如果不使用，将会在三分钟后消失。]",
      - "灵感：学有所成\n我已经准备好改变了。[与“想象”技能一起使用可升级该技能并获得“激情”。五分钟后将退化回“灵感”。]",
      - "名声：秘氛\n离奇之感残留不去。[“秘氛”可能引起猎人注意。猎人没法用它立案调查你，但这会促使他们更努力地寻找证据。]",
      - "名声：邪名\n有些行为会长久留存于人们的记忆中。[“邪名”可能使猎人立案调查你。]",
      - "证据：不确凿证据\n一名猎人发现了我的罪证——或许为真实，或许为臆造。[拥有密教活动“证据”的猎人会变得更加危险。证据在制作它的猎人死后仍继续存在。]",
      - "证据：确凿证据\n“大地啊，开裂吧！哦，不，它不会收容我的。”[掌握密教活动“确凿证据”后，防剿局会以之给你定罪。证据在制作它的猎人死后仍继续存在。]"
    ```

#### excel 梨系牌堆
扩展牌堆应当放置于`extend/deckyaml`路径下，其本质为格式Office的Excel格式表格文件  
详细格式请参考梨系官方


### 自定义帮助文档
`.helpdoc [帮助名称] [帮助内容]`  设置帮助文档  
`.helpdoc [帮助名称]`  删除帮助文档  

这些指令可以调整帮助文档的词条内容，或是增加新的帮助文档，亦或是删除帮助文档，此外，你还可以通过扩展文件进行扩展。  

#### 扩展帮助文档
扩展帮助文档应当放置于`extend/helpdoc`路径下，其本质为格式如下的json文本文件
??? 扩展帮助文档
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
`.strPcSkillCheckFailed 哈哈，失败，哈哈`  
即可将检定失败回复词进行设置。  

#### 多条回复
如果需要回复在多条中随机，则需要使用`|`进行分隔，如：  
`.strRoll 是的，[{tName}]掷骰: {tRollResult}|我发现[{tName}]掷骰:出了{tRollResult}]！`  

#### 牌堆抽取
可以使用类似`{牌堆名称}`的格式对牌堆进行抽取，如：  
`.strBot 欢迎使用本机器人! 请使用[.help]查看帮助 {麻将牌}`

#### 高级自定义
> 以下功能需要`OlivaDiceMaster 大师模块` 和 `ChanceCustom 程心自定义`  

`.master joyEnableCCPK 1`指令可以开启程心自定义模式，这个模式下会将回复词进行基于程心自定义语法的解析。  
完全支持程心自定义的[变量列表](https://forum.olivos.run/p/1)。  

> .strRoll [{tName}]掷骰: {tRollResult} 【牌堆麻将牌】
>   
> 骰子: 回复词[strRoll]已更新
>   
> .rd
>   
> 骰子: [仑质]掷骰: 1D100=1 三筒

#### help指令的自定义回复
需要特别指出的是，`.help`指令回复的内容不属于自定义回复的范畴，而是属于自定义帮助文档，其内容与`help default`一致，可以通过`helpdoc`指令进行设置  

#### 自定义回复表
以下为可以用于`console/customReply.json`文件的内容，其键值对关系也可以用于上文所提到的`str`指令设置  

- OlivaDiceCore 核心模块
??? 核心模块
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
        "strBotExitRemote": "收到远程控制, 即将退出本群，骰主附加消息：{tExtraMsg}",
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
        "strHelpDoc" : "已为[{tUserName}]找到以下条目:\n{tHelpDocResult}",
        "strHelpDocRecommend" : "已为[{tUserName}]找到以下相似条目:\n{tHelpDocResult}",
        "strHelpDocNotFound" : "未找到匹配条目",
        "strDrawTi" : "[{tName}]疯狂发作-临时症状:\n{tResult}",
        "strDrawLi" : "[{tName}]疯狂发作-总结症状:\n{tResult}",
        "strDrawName" : "[{tUserName}]的随机名称:\n{tResult}",
        "strDrawDeck" : "[{tUserName}]抽到了:\n{tDrawDeckResult}",
        "strDrawDeckHideShow" : "[{tUserName}]进行了暗抽牌",
        "strDrawDeckRecommend" : "已为[{tUserName}]找到以下相似牌堆:\n{tDrawDeckResult}",
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
        "strSetGroupRavRule" : "已设置本群RAV判定规则[{tRavRuleName}]{tLazyResult}",
        "strDelGroupRavRule" : "已清除本群RAV判定规则，将使用默认规则（规则1：官方规则）",
        "strSetGroupMainDice" : "已设置本群套用主骰[{tResult}]",
        "strShowGroupMainDice" : "本群已套用主骰[{tResult}]",
        "strShowGroupMainDiceNone" : "本群未设置主骰",
        "strDelGroupMainDice" : "已清除本群套用主骰",
        "strSnSet" : "已将[{tUserName}]的群名片修改为[{tResult}]\n若误设置群名片，请使用指令[.st blockrm 记录]来清除自定义名片\n若需开启自动更改群名片功能，请使用命令[.sn auto on]",
        "strSnPcCardNone" : "[{tUserName}]未设置人物卡，无法进行名片设置",
        "strSnSetAtOther" : "已将[{tUserName01}]的群名片修改为[{tResult}]",
        "strSnPcCardNoneAtOther" : "[{tUserName01}]未设置人物卡，无法进行名片设置",
        "strSnAutoOn" : "[{tUserName}]已开启自动群名片功能，人物卡数值变动时将自动更新群名片",
        "strSnAutoAlreadyOn" : "[{tUserName}]的自动群名片功能已处于开启状态",
        "strSnAutoOff" : "[{tUserName}]已关闭自动群名片功能",
        "strSnAutoAlreadyOff" : "[{tUserName}]的自动群名片功能已处于关闭状态",
        "strPcSetMapValueError" : "[{tResult}]不是合法的表达式",
        "strPcInitSet" : "先攻列表已设置:\n{tResult}",
        "strPcInitShow" : "当前先攻列表（第{tRound}轮）:\n{tResult}",
        "strPcInitReset" : "重新生成先攻列表:\n{tResult}",
        "strPcInitClear" : "已清空先攻列表",
        "strPcInitShowNode" : "{tId}. [{tSubName}]: {tSubResult}",
        "strPcInitShowNodeSpecial" : "-> {tId}. [{tSubName}]: {tSubResult}",
        "strPcInitDel" : "已从先攻列表中删除[{tName}]",
        "strPcInitEnd" : "回合结束！现在轮到[{tSubName}]{tAtUser}行动了！（先攻值：{tSubResult}，第{tRound}轮）",
        "strPcInitEndNoList" : "当前没有先攻列表",
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
        "strPcShow" : "[{tUserName}]的人物卡[{tName}]:\n{tPcShow}\n\n{tDefaultShow}",
        "strPcShowAtOther" : "[{tUserName01}]的人物卡[{tName}]:\n{tPcShow}\n\n{tDefaultShow}",
        "strPcShowNone" : "当前没有人物卡",
        "strPcShowNoneAtOther" : "目标人物没有人物卡",
        "strShowDefaultOn" : "[{tUserName}]已开启非默认值显示模式，st show将只显示与模板默认值不同的技能",
        "strShowDefaultAlreadyOn" : "[{tUserName}]的非默认值显示模式已处于开启状态",
        "strShowDefaultOff" : "[{tUserName}]已关闭非默认值显示模式，st show将显示所有技能",
        "strShowDefaultAlreadyOff" : "[{tUserName}]的非默认值显示模式已处于关闭状态",
        "strDefaultShowOff": "[*]为使用en自动成长技能\n输入[.st defaultshow on]只显示非默认值技能",
        "strDefaultShowOn" : "[*]为使用en自动成长技能\n输入[.st defaultshow off]显示所有技能",
        "strPcList" : "[{tUserName}]的人物卡:\n{tPcList}\n\n当前选择:[{tPcSelection}]",
        "strPcListLocked" : "[{tUserName}]的人物卡:\n{tPcList}\n\n本群选择:[{tPcSelection}]\n全局选择:[{tGlobalPcSelection}]",
        "strPcListNone" : "当前没有人物卡",
        "strPcLock" : "本群人物卡已锁定(当前人物卡：{tName})，其他群切换人物卡将不影响本群人物卡状态，本群切换人物卡也不会影响其他群状态",
        "strPcLockError" : "本群锁定人物卡失败，请重试(当前人物卡：{tName})",
        "strPcLockNone" : "[{tUserName}]未设置人物卡，无法锁定",
        "strPcUnLock" : "本群人物卡锁定已解除(当前人物卡：{tName})，其他群切换人物卡将同步至本群",
        "strPcUnLockNone" : "本群未启用人物卡锁定功能",
        "strPcInitSt" : "人物卡[{tName}]已按照[{tPcTempName}]完成人物卡作成:{tPcInitResult}",
        "strPcSetRecommend" : "未找到人物卡[{tPcSelection}]，你是想找以下人物卡吗？\n{tSearchResult}\n请输入序号以切换对应人物卡",
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
        "strPcSkillCheckNone" : "请指定需要检定的技能",
        "strPcSkillCheckNoneAtOther" : "请指定他人需要检定的技能",
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
        "strHiyResult" : "[{tPcName}]的骰点统计:\n骰点次数：{tTotalRolls}次\n普通成功：{tNormalSuccess}次\n困难成功：{tHardSuccess}次\n极难成功：{tExtremeSuccess}次\n大成功：{tGreatSuccess}次\n失败：{tFail}次\n大失败：{tGreatFail}次\n总成功数：{tTotalSuccess}次\n总失败数：{tTotalFail}次\n成功率：{tSuccessRate}%",
        "strHiyPcNotFound" : "未找到人物卡或未设置人物卡",
        "strSanCheck" : "[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}点,当前剩余[{tSkillValueNew}]点",
        "strSanCheckGreatFailed" : "[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}的最大值[{tRollSubResultIntMax}]点,当前剩余[{tSkillValueNew}]点",
        "strSanCheckError" : "[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n掷骰表达式[{tRollSubResult}]存在错误",
        "strSanCheckAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}点,当前剩余[{tSkillValueNew}]点",
        "strSanCheckGreatFailedAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n理智减少{tRollSubResult}的最大值[{tRollSubResultIntMax}]点,当前剩余[{tSkillValueNew}]点",
        "strSanCheckErrorAtOther" : "[{tUserName}]帮[{tUserName01}]的人物卡[{tName}]进行理智检定[{tSkillValue}]:\n{tRollResult} {tSkillCheckReasult}\n掷骰表达式[{tRollSubResult}]存在错误",
        "strMHOn" : "本群神话淬炼效果已开启",
        "strMHOff" : "本群神话淬炼效果已关闭",
        "strMHAlreadyOn" : "本群神话淬炼效果已经处于开启状态",
        "strMHAlreadyOff" : "本群神话淬炼效果已经处于关闭状态",
        "strMHListEmpty" : "当前没有处于神话淬炼状态的人物卡",
        "strMHList" : "神话淬炼状态人物卡列表:\n{tCardList}",
        "strMHAdd" : "已将人物卡[{tPcName}]添加到神话淬炼状态",
        "strMHAddInvalid" : "人物卡名称无效",
        "strMHDel" : "已将人物卡[{tPcName}]从神话淬炼状态中移除",
        "strMHDelNotFound" : "人物卡[{tPcName}]未在神话淬炼状态中",
        "strMHNeedName" : "请指定人物卡名称",
        "strMHClear" : "已清空所有处于神话淬炼状态的角色卡",
        "strMHClearEmpty" : "没有需要清空的处于神话淬炼状态的角色卡",
        "strMHEffect" : "\n[神话淬炼]理智损失减半: {tOriginalLoss} -> {tActualLoss}",
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
        "strObJoin" : "[{tUserName}]现已加入旁观，若你已添加机器人为好友，暗骰结果将发送给你。同时，若你已开启自动群名片功能[.sn auto on]，你的群名片也会被修改为[ob_{tUserName}]",
        "strObJoinAlready" : "[{tUserName}]已在旁观中",
        "strObExit" : "[{tUserName}]现已退出旁观，若你已开启自动群名片功能[.sn auto on]，群名片将被修改为[{tUserName}]",
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
        "strTeamCheckResultNone": "请指定小队需要检定的技能",
        "strTeamSCResult": "小队[{tTeamName}]进行理智检定:\n{tResult}",
        "strTeamRoll": "小队[{tTeamName}]掷骰:\n{tRollResult}",
        "strTeamRollWithReason": "小队[{tTeamName}]由于[{tReason}]掷骰:\n{tRollResult}",
        "strTeamSetRecommend" : "未找到小队[{tTeamName}]，你是想找以下小队吗？\n{tSearchResult}\n请输入序号以切换对应小队",
        "strNoActiveTeam": "当前群组没有活跃小队",
        "strTeamNotFound": "小队[{tTeamName}]不存在",
        "strNoTeams": "当前群组没有创建任何小队",
        "strNoMembersRemoved": "没有移除任何成员",
        "strTeamEmpty": "小队[{tTeamName}]中没有成员",
        "strTeamMemberFormat": "[{tUserName}] - [{tPcName}]",
        "strTeamMemberFormatWithIndex": "成员{tIndex}: [{tUserName}] - 人物卡: [{tPcName}]",
        "strTeamSortMemberFormat": "{tIndex}. [{tUserName}] - [{tPcName}]({tSkillName}: {tSkillValue})",
        "strTeamCheckMemberFormat": "{tDisplayName}({tSkillName}: {tSkillValue}): {tDiceDetail}/{tSkillValue} {tResult}",
        "strTeamCheckMemberFormatNoSkill": "{tDisplayName}: {tDiceDetail}/{tSkillValue} {tResult}",
        "strTeamSCMemberFormat": "{tDisplayName}(SAN:{tCurrentSan}): {tDiceDetail}/{tCurrentSan}\nSAN: {tCurrentSan} -> {tNewSan}(损失{tSanLoss}点)",
        "strTeamSkillUpdateMemberFormat": "-> [{tUserName}] - [{tPcName}]",
        "strTeamSkillUpdateResultFormat": "{tSkillName}: {tDetail}",
        "strTeamRollMemberFormat": "[{tUserName}] - [{tPcName}]: {tRollResult}",
    }
    ```

- OlivaDiceLogger 日志模块
??? 日志模块
    ```json
    {
        "strLoggerLogOn": "开始记录日志 [{tLogName}] (UUID: {tLogUUID})",
        "strLoggerLogAlreadyOn": "已经正在记录日志 [{tLogName}]",
        "strLoggerLogContinue": "继续记录日志 [{tLogName}] (UUID: {tLogUUID})\n当前已记录 {tLogLines} 行，日志总时长: {tLogTime})",
        "strLoggerLogInvalidName": "日志名称 [{tLogName}] 不合法",
        "strLoggerLogOff": "暂停记录日志 [{tLogName}] (UUID: {tLogUUID})\n当前已记录 {tLogLines} 行，日志总时长: {tLogTime}",
        "strLoggerLogAlreadyOff": "没有正在进行的日志",
        "strLoggerLogEnd": "结束记录日志 [{tLogName}] (当前已记录 {tLogLines} 行，日志总时长: {tLogTime})",
        "strLoggerLogAlreadyEnd": "没有正在进行的日志",
        "strLoggerLogEndingInProgress": "正在处理日志结束操作，请稍候……",
        "strLoggerLogUploadTimeout": "日志 [{tLogName}] (UUID: {tLogUUID}) 上传超时，已自动保存。您可以稍后使用 .log upload {tLogUUID} 手动上传",
        "strLoggerLogSave": "日志 [{tLogName}] (UUID: {tLogUUID}) 已保存",
        "strLoggerLogUrl": "日志已上传，请在[ {tLogUrl} ]提取日志",
        "strLoggerLogList": "本群有以下日志:\n{tLogList}",
        "strLoggerLogListEmpty": "本群暂无日志",
        "strLoggerLogStop": "已强制停止日志 [{tLogName}] (UUID: {tLogUUID}) (当前已记录 {tLogLines} 行，日志总时长: {tLogTime})",
        "strLoggerLogStopUnlock": "已解除日志结束锁定状态",
        "strLoggerLogStopError": "已强制停止日志 [{tLogName}] (UUID: {tLogUUID}) (日志已损坏)",
        "strLoggerLogActiveSwitch": "已切换活跃日志为 [{tLogName}]",
        "strLoggerLogSetRecommend": "未找到日志[{tLogSelection}]，你是想找以下日志吗？:\n{tSearchResult}\n请输入序号以选择对应日志",
        "strLoggerLogUploadNoName": "请指定要上传的日志的UUID",
        "strLoggerLogFileNotFound": "未找到[{tLogUUID}]对应的日志文件",
        "strLoggerLogUploadSuccess": "日志 [{tLogName}](UUID: {tLogUUID}) 重新上传成功，日志总时长: {tLogTime}，请在[ {tLogUrl} ]提取日志",
        "strLoggerLogUploadFailed": "日志 [{tLogName}](UUID: {tLogUUID}) 重新上传失败，请稍后再试",
        "strLoggerLogGenerateNoUUID": "请指定要生成日志的UUID",
        "strLoggerLogGenerateNotFound": "未找到UUID为[{tLogUUID}]的日志文件",
        "strLoggerLogGenerateSuccess": "已成功为UUID [{tLogUUID}] (日志名称: {tLogName}) 生成trpglog文件",
        "strLoggerLogGenerateFailed": "为UUID [{tLogUUID}] 生成trpglog文件失败",
        "strLoggerLogNameNotFound": "本群日志列表中未找到名称为[{tLogName}]的日志",
        "strLoggerLogTempSuccess": "临时日志 [{tLogName}] (UUID: {tLogUUID}) 上传成功，日志总时长: {tLogTime}，请在[ {tLogUrl} ]提取日志",
        "strLoggerLogTempFailed": "临时日志 [{tLogName}] (UUID: {tLogUUID}) 上传失败，请稍后再试",
        "strLoggerLogNotFound": "未找到日志 [{tLogName}]",
        "strLoggerLogRenameSuccess": "日志 [{tLogOldName}] 已重命名为 [{tLogNewName}]",
        "strLoggerLogRenameActiveSuccess": "当前活动日志 [{tLogOldName}] 已重命名为 [{tLogNewName}]",
        "strLoggerLogRenameSameName": "新名称 [{tLogName}] 与旧日志名称相同",
        "strLoggerLogRenameNameExists": "日志名称 [{tLogName}] 已存在",
        "strLoggerLogInfo": "[{tLogName}] 日志状态:\nUUID: {tLogUUID}\n当前状态: {tLogInfo}\n日志行数: {tLogLines}\n日志总时长: {tLogTime}",
        "strLoggerLogInfoNoLog": "当前没有活跃日志",
        "strLoggerLogQuote": "此处为 [{tLogName}] 日志结束消息",
        "strLoggerLogQuoteError": "[{tLogName}] 日志引用失败，可能原因是平台不为QQ或者Bot未记录上次结束日志的消息",
        "strLoggerLogQuoteOn": "本群已开启自动引用上次结束日志功能",
        "strLoggerLogQuoteAlreadyOn": "本群自动引用上次结束日志功能已处于开启状态",
        "strLoggerLogQuoteOff": "本群已关闭自动引用上次结束日志功能",
        "strLoggerLogQuoteAlreadyOff": "本群自动引用上次结束日志功能已处于关闭状态"
    }
    ```

- OlivaDiceMaster 大师模块
??? 大师模块
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
        "strMasterOopmGet": "{tMasterOopkNameList}\n模块已安装成功，请使用[.system restart]应用安装",
        "strMasterOopmGetNone": "{tMasterOopkNameList}\n模块不存在，请先使用[.oopm list]指令查看受支持的模块",
        "strMasterOopmGetSkipSrc": "{tMasterOopkNameList}\n模块为手动部署模式，已跳过",
        "strMasterOopmDownloadFailed": "{tMasterOopkNameList}\n模块下载失败",
        "strMasterOopmCopyFailed": "{tMasterOopkNameList}\n模块安装失败",
        "strMasterSendFromMaster": "来自Master的消息：\n{tResult}",
        "strMasterSendToMaster": "[{tGroupName}]({tGroupId})中[{tUserName}]({tUserId})发来的消息：\n{tResult}",
        "strMasterSendToMasterAlready": "已将消息发送至Master",
        "strMasterTrustSet": "[{tName}]({tId})的{tMasterTrustName}已设置为：{tResult}",
        "strMasterTrustGet": "[{tName}]({tId})的{tMasterTrustName}为：{tResult}",
        "strMasterPlatformNo": "该功能在此平台不受支持",
        "strMasterGroupClearShow": "已检查[{tMasterCount01}]个群:\n{tResult}\n已经决定清除[{tMasterCount02}]个群\n请使用[.group clear do (天数)]指令执行这项操作",
        "strMasterGroupClearShowOff": "已检查[{tMasterCount01}]个群:\n{tResult}\n已经决定清除[{tMasterCount02}]个群\n请使用[.group clear do off]指令执行这项操作",
        "strMasterGroupClearDoUnit": "已经清除群:\n{tResult}",
        "strMasterGroupClearDoUnitSend": "检测到在此处最后发言为{tResult}，即将自动退出",
        "strMasterGroupClearDo": "已检查[{tMasterCount01}]个群\n已经清除[{tMasterCount02}]个群",
        "strMasterGroupClearUnit": "[{tName}] - ({tId}): {tResult}",
        "strMasterBackupStart": "正在开始备份数据...",
        "strMasterBackupSuccess": "数据备份完成：\n{tBackupResult}",
        "strMasterBackupFailed": "数据备份失败：\n{tBackupResult}",
        "strMasterBackupConfigSet": "配置项 {tConfigKey} 已设置为: {tConfigValue}",
        "strMasterBackupConfigSetFailed": "配置项设置失败：\n{tBackupResult}",
        "strMasterBackupChangeUsage": "用法: .backup change 配置项 配置值\n可用配置项: startDate, passDay, backupTime, maxBackupCount, isBackup",
        "strMasterBackupConfigGet": "配置项 {tConfigKey}: {tConfigValue}",
        "strMasterBackupConfigNotFound": "配置项 {tConfigKey} 不存在或未设置",
        "strMasterBackupInfo": "{tBackupResult}",
        "strMasterAccountLinkSuccess": "已成功建立主从关系：\n{tAccountResult}",
        "strMasterAccountLinkFailed": "建立主从关系失败：\n{tAccountResult}",
        "strMasterAccountUnlinkSuccess": "已成功断开主从关系：\n{tAccountResult}",
        "strMasterAccountUnlinkFailed": "断开主从关系失败：\n{tAccountResult}",
        "strMasterAccountList": "{tAccountResult}",
        "strMasterAccountShow": "{tAccountResult}",
        "strMasterAccountImportSuccess": "数据导入成功：\n{tAccountResult}",
        "strMasterAccountImportFailed": "数据导入失败：\n{tAccountResult}",
        "strMasterAccountExportSuccess": "数据导出成功：\n{tAccountResult}",
        "strMasterAccountExportFailed": "数据导出失败：\n{tAccountResult}"
    }
    ```

- OlivaDiceOdyssey 高阶模块
??? 高阶模块
    ```json
    {
        "strOdysseyCnmodsSearch": "魔都模组搜索结果如下:\n{tCnmodsResult}",
        "strOdysseyCnmodsRec": "魔都模组编辑推荐结果如下:\n{tCnmodsResult}",
        "strOdysseyCnmodsAuthor": "作者模组搜索结果如下:\n{tCnmodsResult}",
        "strOdysseyCnmodsLuck": "魔都模组随机如下:\n{tCnmodsResult}",
        "strOdysseyCnmodsSearchNotFound": "未找到相关魔都模组搜索结果",
        "strOdysseyCnmodsRecNotFound": "未找到相关魔都模组编辑推荐结果",
        "strOdysseyCnmodsAuthorNotFound": "未找到该作者的魔都模组",
        "strOdysseyCnmodsLuckNotFound": "未找到魔都模组推荐结果",
        "strOdysseyCnmodsFindNotFound": "未找到该模组(keyId: {tKeyId})",
        "strOdysseyCnmodsFindError": "获取模组详情失败",
        "strOdysseyCnmodsFindErrorRetry": "获取模组详情失败，请稍后再试",
        "strOdysseyCnmodsFindOnlyNumber": "find命令只接受纯数字keyId\n例如: .cnmods find 12345",
        "strOdysseyCnmodsGetCacheNotFound": "未找到缓存的模组列表\n或许你应当先试试查找模组",
        "strOdysseyCnmodsGetRangeError": "序号超出范围(1-{tRange})\n或许你应当先试试查找模组",
        "strOdysseyCnmodsGetSearchNotFound": "未找到相关魔都模组",
        "strOdysseyCnmodsGetSearchError": "搜索失败，请稍后再试",
        "strOdysseyCnmodsGetMultiMatch": "找到[{tCount}]个匹配的模组:\n{tCnmodsResult}",
        "strOdysseyRulesNone": "没有找到合适的规则",
        "strOdysseyRulesShow": "规则速查结果如下:\n{tResult}",
        "strOdysseyRulesList": "规则速查找到如下待选结果:\n{tResult}\n输入序号以查看对应结果",
        "strOdysseyRulesSplit": "\n",
        "strOdysseyRulesError": "规则速查发生错误:\n{tResult}",
        "strOdysseyKOOKBotMarketPulseUUID": "-",
        "strOdysseyKOOKPlayGameMusicName": "-",
        "strOdysseyKOOKPlayGameMusicSinger": "-",
        "strOdysseyKOOKPlayGameID": "6"
    }
    ```

- OlivaDiceJoy 娱乐模块
??? 娱乐模块
    ```json
    {
        "strJoyJrrp": "[{tUserName}]的今日人品为[{tJrrpResult}]",
        "strJoyZrrp": "[{tUserName}]的昨日人品为[{tJrrpResult}]",
        "strJoyMrrp": "[{tUserName}]的明日人品为[{tJrrpResult}]",
        "strJoyPokeCustom": "[{tUserName}]你好，这里是青果核心OlivaDice。"
    }
    ```

- OlivaStoryCore 故事引擎模块
??? 故事引擎模块
    ```json
    {
        "strStoryCoreStoryTall": "{tStoryCoreResult}\n\n{tStoryCoreSelection}",
        "strStoryCoreStoryTallNone": "故事不存在",
        "strStoryCoreStoryTallBreak": "故事中断了",
        "strStoryCoreStoryTallEnd": "故事结束了",
        "strStoryCoreStoryRecommend": "未找到故事，您可能想要的是：\n{tStoryCoreRecommend}"
    }
    ```

### 自定义人物卡模板
青果核心在底层将主骰表达式、检定规则、人物卡作成、技能初始化、技能分类等一系列会随着规则发生变化的设置，统合成了与人物卡绑定的人物卡模板功能，可以通过`.st temp`与`.st rule`指令来进行切换。OlivOS已经内置了`default`、`COC7`、`DND5E`、`FATE`、`DX3`、`COC6`等人物卡模板。  
与此同时，人物卡模板还可以通过扩展文件的方式进行扩展，该部分的详细说明请查看[自定义人物卡模板编写指南](/OlivaDice3_Master_Manual_pcTemplate)，以下为可以用于`template/`目录的人物卡模板文件内容：  
??? 人物卡模板扩展文件
    ```json
    {
        "default": {
            "mainDice": "1D100",
            "customDefault": {
                "d": {
                    "leftD": 1,
                    "rightD": 100,
                    "sub": {
                        "k": null,
                        "q": null,
                        "p": null,
                        "b": null
                    },
                    "subD": {
                        "p": 1,
                        "b": 1
                    }
                }
            },
            "skill": {
                "属性": [
                    "STR",
                    "CON",
                    "SIZ",
                    "DEX",
                    "APP",
                    "INT",
                    "POW",
                    "EDU",
                    "LUC",
                    "SAN",
                    "SANMAX",
                    "HP",
                    "HPMAX",
                    "MP",
                    "MPMAX",
                    "IDEA",
                    "KNOW",
                    "HPMAXADD",
                    "MPMAXADD",
                    "SANMAXADD"
                ],
                "技能": [
                    "会计",
                    "人类学",
                    "估价",
                    "考古学",
                    "取悦",
                    "攀爬",
                    "计算机使用",
                    "信用",
                    "克苏鲁神话",
                    "乔装",
                    "闪避",
                    "汽车驾驶",
                    "电气维修",
                    "电子学",
                    "话术",
                    "急救",
                    "历史",
                    "恐吓",
                    "跳跃",
                    "法律",
                    "图书馆",
                    "聆听",
                    "锁匠",
                    "机械维修",
                    "医学",
                    "博物",
                    "导航",
                    "神秘学",
                    "操作重型机械",
                    "说服",
                    "精神分析",
                    "心理学",
                    "骑乘",
                    "妙手",
                    "侦查",
                    "潜行",
                    "游泳",
                    "投掷",
                    "追踪",
                    "驯兽",
                    "潜水",
                    "爆破",
                    "读唇",
                    "催眠",
                    "炮术",
                    "母语",
                    "鞭子",
                    "电锯",
                    "链枷",
                    "绞具",
                    "斧",
                    "剑",
                    "矛",
                    "手枪",
                    "步霰",
                    "冲锋枪",
                    "弓术",
                    "喷射器",
                    "机枪",
                    "重武器",
                    "表演",
                    "喜剧",
                    "美术",
                    "摄影",
                    "伪造",
                    "写作",
                    "书法",
                    "乐理",
                    "厨艺",
                    "裁缝",
                    "理发",
                    "建筑",
                    "舞蹈",
                    "酿酒",
                    "捕鱼",
                    "歌唱",
                    "制陶",
                    "雕塑",
                    "杂技",
                    "风水",
                    "技术制图",
                    "耕作",
                    "打字",
                    "速记",
                    "木匠",
                    "莫里斯舞蹈",
                    "歌剧歌唱",
                    "粉刷匠与油漆工",
                    "吹真空管",
                    "飞行器",
                    "船",
                    "地质学",
                    "化学",
                    "生物学",
                    "数学",
                    "天文学",
                    "物理学",
                    "药学",
                    "植物学",
                    "动物学",
                    "密码学",
                    "工程学",
                    "气象学",
                    "司法科学",
                    "斗殴",
                    "生存",
                    "中文",
                    "英语",
                    "法语",
                    "德语",
                    "俄语",
                    "西班牙语",
                    "拉丁语",
                    "希腊语",
                    "阿拉伯语",
                    "日语",
                    "韩语",
                    "意大利语",
                    "葡萄牙语",
                    "希伯来语",
                    "梵语",
                    "埃及语",
                    "苏美尔语",
                    "阿卡德语",
                    "藏语",
                    "拉莱耶语",
                    "米戈语",
                    "深潜者语",
                    "旧印语",
                    "奈亚拉托提普的低语",
                    "手语",
                    "兽语"
                ]
            },
            "skillConfig": {
                "skipEnhance": [
                    "STR",
                    "CON",
                    "SIZ",
                    "DEX",
                    "APP",
                    "INT",
                    "POW",
                    "EDU",
                    "LUC",
                    "SAN",
                    "SANMAX",
                    "HP",
                    "HPMAX",
                    "MP",
                    "MPMAX",
                    "IDEA",
                    "KNOW",
                    "HPMAXADD",
                    "MPMAXADD",
                    "SANMAXADD",
                    "MOV",
                    "克苏鲁神话",
                    "信用"
                ],
                "forceMapping": [
                    "SANMAX",
                    "HPMAX",
                    "MPMAX"
                ]
            },
            "init": {
                "STR": "3d6x5",
                "CON": "3d6x5",
                "SIZ": "(2d6+6)x5",
                "DEX": "3d6x5",
                "APP": "3d6x5",
                "INT": "(2d6+6)x5",
                "POW": "3d6x5",
                "EDU": "(2d6+6)x5",
                "LUC": "3d6x5"
            },
            "mapping": {
                "闪避": "({DEX})/2",
                "母语": "{EDU}",
                "SAN": "({POW})",
                "SANMAX": "99-({克苏鲁神话})+({SANMAXADD})",
                "HP": "(({CON})+({SIZ}))/10",
                "HPMAX": "(({CON})+({SIZ}))/10+({HPMAXADD})",
                "MP": "({POW})/5",
                "MPMAX": "({POW})/5+({MPMAXADD})"
            },
            "synonyms":{
                "STR": ["力量", "STR"],
                "CON": ["体质", "CON"],
                "SIZ": ["体型", "SIZ"],
                "DEX": ["敏捷", "DEX"],
                "APP": ["外貌", "APP"],
                "INT": ["智力", "INT"],
                "POW": ["意志", "POW"],
                "EDU": ["教育", "EDU"],
                "LUC": ["幸运", "LUC", "运气", "LUK"],
                "SAN": ["理智", "SAN","Sanity","SAN值","理智值"],
                "SANMAX": ["理智上限", "SANMAX","SanityMAX"],
                "HP": ["生命值","体力","HP","HitPoints","生命","血量"],
                "HPMAX": ["生命值上限","HPMAX","HitPointsMAX","生命上限","血量上限","体力上限"],
                "MP": ["魔法","MP","MagicPoints"],
                "MPMAX": ["魔法上限","MPMAX","MagicPointsMAX"],
                "SANMAXADD": ["SANMAXADD","理智上限加值"],
                "HPMAXADD": ["HPMAXADD","生命值上限加值","生命上限加值","血量上限加值","体力上限加值"],
                "MPMAXADD": ["MPMAXADD","魔法上限加值"],
                "MOV": ["MOV","MOVE","移动速度","移动力"],
                "IDEA": ["灵感", "IDEA"],
                "KNOW": ["知识", "KNOW"],
                "MOV": ["移动力","MOV"],
                "会计": ["会计","Accounting"],
                "人类学": ["人类学","Anthropology"],
                "估价": ["估价","Aooraise"],
                "考古学": ["考古学","Archaeology"],
                "取悦": ["取悦","魅惑","Charm"],
                "攀爬": ["攀爬","Climb"],
                "计算机使用": ["计算机使用","计算机","电脑","电脑使用","Computer_Use"],
                "信用": ["信用评级","CR","信誉","信用度","信用","信誉度","Credit_Rating"],
                "克苏鲁神话": ["克苏鲁神话","CM","克苏鲁","Cthulhu_Mythos","克神","克话"],
                "乔装": ["乔装","Disguise"],
                "闪避": ["闪避","Dodge"],
                "汽车驾驶": ["汽车驾驶","驾驶","汽车","Drive_Auto"],
                "电气维修": ["电气维修","电器维修","Electical_Repair"],
                "电子学": ["电子学","Electronics"],
                "话术": ["话术","快速交谈","Fast_Talk"],
                "急救": ["急救","First_Aid"],
                "历史": ["历史","History"],
                "恐吓": ["恐吓","Intimidate"],
                "跳跃": ["跳跃","Jump"],
                "法律": ["法律","Law"],
                "图书馆": ["图书馆使用","图书馆","Library_Use"],
                "聆听": ["聆听","Listen"],
                "锁匠": ["锁匠","Locksmith","开锁","撬锁"],
                "机械维修": ["机械维修","Mechanical_Repair"],
                "医学": ["医学","Medicine"],
                "博物": ["博物", "博物学","自然学","自然史","Natural_World"],
                "导航": ["导航","领航","Navigate"],
                "神秘学": ["神秘学","Occult"],
                "操作重型机械": ["操作重型机械","重型机械","Operate_Heavy_Machinery","重型操作","重型"],
                "说服": ["说服","Persuade"],
                "精神分析": ["精神分析","Psychoanalysis"],
                "心理学": ["心理学","Psychology"],
                "骑乘": ["骑术","骑乘","Ride"],
                "妙手": ["妙手","Sleight_of_Hand"],
                "侦查": ["侦查","侦察","Spot_Hidden"],
                "潜行": ["潜行","Stealth"],
                "游泳": ["游泳","Swim"],
                "投掷": ["投掷","Throw"],
                "追踪": ["追踪","Track"],
                "驯兽": ["驯兽","Beast_Training","动物驯养"],
                "潜水": ["潜水","Diving"],
                "爆破": ["爆破","Demolitions"],
                "读唇": ["读唇","Read_Lips"],
                "催眠": ["催眠","Hypnosis"],
                "炮术": ["炮术","Artillery"],
                "母语": ["母语", "Own_Language"],
                "鞭子": ["鞭子", "Whip", "鞭"],
                "电锯": ["电锯", "Chainsaw", "链锯"],
                "链枷": ["链枷", "Flail", "连枷"],
                "绞具": ["绞具", "Garrote", "绞索"],
                "斧": ["斧", "Axe"],
                "剑": ["剑", "Sword"],
                "矛": ["矛", "Spear"],
                "手枪": ["手枪", "Handgun"],
                "步霰": ["步霰", "Rifle_Shotgun", "步枪", "Rifle", "霰弹枪", "Shotgun", "霰弹", "散弹", "散弹枪"],
                "冲锋枪": ["冲锋枪", "Submachine_Gun"],
                "弓术": ["弓术", "Archery", "弓"],
                "喷射器": ["喷射器", "Flamethrower", "火焰喷射器"],
                "机枪": ["机枪", "Machine_Gun"],
                "重武器": ["重武器", "Heavy_Weapons"],
                "表演": ["表演", "Acting"],
                "喜剧": ["喜剧", "Comedy"],
                "美术": ["美术", "Art"],
                "摄影": ["摄影", "Photography"],
                "伪造": ["伪造", "Forgery"],
                "写作": ["写作", "Writing"],
                "书法": ["书法", "Calligraphy"],
                "乐理": ["乐理", "Music"],
                "厨艺": ["厨艺", "Cooking"],
                "裁缝": ["裁缝", "Tailor"],
                "理发": ["理发", "Barber"],
                "建筑": ["建筑", "Architecture"],
                "舞蹈": ["舞蹈", "Dance"],
                "酿酒": ["酿酒", "Brewing"],
                "捕鱼": ["捕鱼", "Fishing"],
                "歌唱": ["歌唱", "Sing"],
                "制陶": ["制陶", "Pottery"],
                "雕塑": ["雕塑", "Sculpture"],
                "杂技": ["杂技", "Acrobatics"],
                "风水": ["风水", "Feng_Shui"],
                "技术制图": ["技术制图", "Technical_Drawing"],
                "耕作": ["耕作", "Farming"],
                "打字": ["打字", "Typing"],
                "速记": ["速记", "Shorthand"],
                "木匠": ["木匠", "Carpentry"],
                "莫里斯舞蹈": ["莫里斯舞蹈", "Morris_Dance"],
                "歌剧歌唱": ["歌剧歌唱", "Opera_Singing"],
                "粉刷匠与油漆工": ["粉刷匠与油漆工", "Painting_Decorating", "粉刷匠和油漆工"],
                "吹真空管": ["吹真空管", "Vacuum_Tube_Repair"],
                "飞行器": ["飞行器", "Pilot_Aircraft"],
                "船": ["船", "Boat"],
                "地质学": ["地质学", "Geology"],
                "化学": ["化学", "Chemistry"],
                "生物学": ["生物学", "Biology"],
                "数学": ["数学", "Mathematics"],
                "天文学": ["天文学", "Astronomy"],
                "物理学": ["物理学", "Physics"],
                "药学": ["药学", "Pharmacy"],
                "植物学": ["植物学", "Botany"],
                "动物学": ["动物学", "Zoology"],
                "密码学": ["密码学", "Cryptography"],
                "工程学": ["工程学", "Engineering"],
                "气象学": ["气象学", "Meteorology"],
                "司法科学": ["司法科学", "Forensic_Science"],
                "斗殴": ["斗殴", "Brawl"],  
                "生存": ["生存", "Survival"],
                "中文": ["中文", "Chinese"],
                "英语": ["英语", "English"],
                "法语": ["法语", "French"],
                "德语": ["德语", "German"],
                "俄语": ["俄语", "Russian"],
                "西班牙语": ["西班牙语", "Spanish"],
                "拉丁语": ["拉丁语", "Latin"],
                "希腊语": ["希腊语", "Greek"],
                "阿拉伯语": ["阿拉伯语", "Arabic"],
                "日语": ["日语", "Japanese"],
                "韩语": ["韩语", "Korean"],
                "意大利语": ["意大利语", "Italian"],
                "葡萄牙语": ["葡萄牙语", "Portuguese"],
                "希伯来语": ["希伯来语", "Hebrew"],
                "梵语": ["梵语", "Sanskrit"],
                "埃及语": ["埃及语", "Egyptian"],
                "苏美尔语": ["苏美尔语", "Sumerian"],
                "阿卡德语": ["阿卡德语", "Akkadian"],
                "藏语": ["藏语", "Tibetan"],
                "拉莱耶语": ["拉莱耶语", "R\"lyehian"],
                "米戈语": ["米戈语", "MiGo"],
                "深潜者语": ["深潜者语", "Deep_One"],
                "旧印语": ["旧印语", "Elder_Sign"],
                "奈亚拉托提普的低语": ["奈亚拉托提普的低语", "Nyarlathotep\"s_Whispers"],
                "手语": ["手语", "Sign_Language"],
                "兽语": ["兽语", "Animal_Tongue"]
            },
            "redirect": {
                "力量": "STR",
                "体质": "CON",
                "体型": "SIZ",
                "敏捷": "DEX",
                "外貌": "APP",
                "智力": "INT",
                "意志": "POW",
                "教育": "EDU",
                "幸运": "LUC",
                "理智": "SAN",
                "灵感": "IDEA",
                "知识": "KNOW",
                "移动速度": "MOV"
            },
            "showName": {
                "STR": "力量",
                "CON": "体质",
                "SIZ": "体型",
                "DEX": "敏捷",
                "APP": "外貌",
                "INT": "智力",
                "POW": "意志",
                "EDU": "教育",
                "LUC": "幸运",
                "IDEA": "灵感",
                "KNOW": "知识",
                "MOV": "移动速度"
            },
            "snTitle": "{tName} hp{HP}/{HPMAX} san{SAN}/{SANMAX} dex{DEX}",
            "defaultSkillValue": {
                "会计": 5,
                "人类学": 1,
                "估价": 5,
                "考古学": 1,
                "取悦": 15,
                "攀爬": 20,
                "计算机使用": 5,
                "信用": 0,
                "克苏鲁神话": 0,
                "乔装": 5,
                "汽车驾驶": 20,
                "电气维修": 10,
                "电子学": 1,
                "话术": 5,
                "急救": 30,
                "历史": 5,
                "恐吓": 15,
                "跳跃": 20,
                "法律": 5,
                "图书馆": 20,
                "聆听": 20,
                "锁匠": 1,
                "机械维修": 10,
                "医学": 1,
                "博物": 10,
                "导航": 10,
                "神秘学": 5,
                "操作重型机械": 1,
                "说服": 10,
                "精神分析": 1,
                "心理学": 10,
                "骑乘": 5,
                "妙手": 10,
                "侦查": 25,
                "潜行": 20,
                "游泳": 20,
                "投掷": 20,
                "追踪": 10,
                "驯兽": 5,
                "潜水": 1,
                "爆破": 1,
                "读唇": 1,
                "催眠": 1,
                "炮术": 1,
                "手枪": 20,
                "步霰": 25,
                "斗殴": 25,
                "书法": 5,
                "伪造": 5,
                "写作": 5,
                "冲锋枪": 15,
                "制陶": 5,
                "剑": 20,
                "动物学": 1,
                "化学": 1,
                "厨艺": 5,
                "司法科学": 1,
                "吹真空管": 5,
                "喜剧": 5,
                "乐理": 5,
                "地质学": 1,
                "天文学": 1,
                "密码学": 1,
                "工程学": 1,
                "弓术": 15,
                "技术制图": 5,
                "摄影": 5,
                "数学": 10,
                "斧": 15,
                "木匠": 5,
                "机枪": 10,
                "植物学": 1,
                "歌剧歌唱": 5,
                "气象学": 1,
                "喷射器": 10,
                "物理学": 1,
                "理发": 5,
                "生存": 10,
                "生物学": 1,
                "矛": 20,
                "科学": 1,
                "粉刷匠与油漆工": 5,
                "绞具": 15,
                "美术": 5,
                "耕作": 5,
                "舞蹈": 5,
                "船": 1,
                "药学": 1,
                "莫里斯舞蹈": 5,
                "表演": 5,
                "裁缝": 5,
                "链枷": 10,
                "速记": 5,
                "重武器": 10,
                "电锯": 10,
                "雕塑": 5,
                "鞭子": 5,
                "飞行器": 1,
                "SANMAX": 99,
                "SANMAXADD": 0,
                "HPMAXADD": 0,
                "MPMAXADD": 0
            },
            "checkRules": {
                "default": {
                    "checkList": [
                        "success",
                        "hardSuccess",
                        "extremeHardSuccess",
                        "greatSuccess",
                        "fail",
                        "greatFail"
                    ],
                    "success": {
                        ".<=": ["$roll", "$skill"]
                    },
                    "fail": {
                        ".>": ["$roll", "$skill"]
                    },
                    "hardSuccess": {
                        ".<=": [
                            "$roll",
                            {
                                "./": ["$skill", 2]
                            }
                        ]
                    },
                    "extremeHardSuccess": {
                        ".<=": [
                            "$roll",
                            {
                                "./": ["$skill", 5]
                            }
                        ]
                    },
                    "greatSuccess": {
                        ".==": ["$roll", 1]
                    },
                    "greatFail": {
                        ".or": [
                            {
                                ".and": [
                                    {
                                        ".<": ["$skill", 50]
                                    },
                                    {
                                        ".>=": ["$roll", 96]
                                    },
                                    {
                                        ".<=": ["$roll", 100]
                                    }
                                ]
                            },
                            {
                                ".and": [
                                    {
                                        ".>=": ["$skill", 50]
                                    },
                                    {
                                        ".==": ["$roll", 100]
                                    }
                                ]
                            }
                        ]
                    }
                }
            }
        }
    }
    ```


### 自定义指令/自定义问答/reply
青果核心将类似 塔系和溯洄系 的自定义问答功能(reply)与自定义指令功能单独集成为了一个OlivOS插件——[程心自定义](https://forum.olivos.run/p/1)，其实际上已经是铃心自定义的重做版本，相比旧时代传统的骰子内置的`reply功能`更加完备，功能更加强大。  

你可以在任务栏右下角托盘区域，找到OlivOS的图标，`右键`打开菜单后 `插件菜单 > 程心自定义 > 设置`，来打开这个插件的设置面板。  
