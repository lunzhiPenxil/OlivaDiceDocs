## Oliva Dice! 手册

*For Oliva.1.2.4*

欢迎使用由`仑质(BenzenPenxil)`所发布的`青果扩充核心 Oliva Dice!`，在使用本核心前，你应当已经是一个能够处理较为复杂问题的骰主，并且已经充分阅读了[Dice! Version 2 文档](https://v2docs.kokona.tech)，如果没有，请先阅读那份文档，本文档将不会对官方文档中所提到的各类特性进行说明。

`青果扩充核心 Oliva Dice!`是由`仑质(BenzenPenxil)`基于已有的Dice!V2核心进行代码层的修改后进行发布的非官方版本，该项目的代码仓库与分支地址为[lunzhiPenxil/Dice - Oliva](https://github.com/lunzhiPenxil/Dice/tree/Oliva)。
该版本核心会引入一些本人认为足够好，同时又不够成熟到提交到官方版本的功能，并针对一些特定场景进行优化，如果你不清楚这些改动的意图与初衷，或者觉得这些改动不符合你的想法，请确保你能够以**合理的方式清晰有条理地**使用`现代汉语(简体中文 - 北京)`提出意见，否则请认为 **“这个垃圾的修改版本实在是太难用了！我还是继续用官方版本比较好”** 

想要获取最新当前最新版本，请在此处下载：    
- [Oliva Dice!](https://github.com/lunzhiPenxil/OlivaDiceDocs/raw/master/_release/564-Oliva.1.2.4_20200729002.zip)    
- [Oliva Dice! for Mirai 整合包](https://github.com/lunzhiPenxil/OlivaDiceDocs/raw/master/_release/Dice%20for%20Mirai%20OlivaBranch%2020200802001.zip)    
或者你可以使用备用链接：    
- [Oliva Dice! - 青果云](http://pan.benzencloudhk.xyz/s/0g9q35i7)  密码：`LOVEOLIVA`    
- [Oliva Dice! for Mirai 整合包 - 青果云](http://pan.benzencloudhk.xyz/s/v4wor8et)  密码：`LOVEOLIVA`    

本核心扩充功能如下：

### 优化过的黑名单相关机制
#### Dicelist相关调整
原版的Dice! 核心在某版本引入了Dicelist概念，这是一种为黑名单信息广播所设计的自动授权系统，由简单的静态页面API实现信息的发布，核心会在初始化阶段拉取相关API的信息以设置本机的Dicelist名单，将会在`BelieveDicelist`项为1时接受该名单上的账号所发送的黑名单信息，该API的具体地址为：[http://shiki.stringempty.xyz/DiceList/](http://shiki.stringempty.xyz/DiceList/)
本核心在此基础上引入了一个基于Github Pages的静态页面API，地址为：[http://benzenpenxil.xyz/Oliva-DiceList/](http://benzenpenxil.xyz/Oliva-DiceList/)
**并且设置了相关配置项用于调整Dicelist的拉取**

#### 上传云记录相关调整
原版的Dice! 核心在某版本引入了对于黑名单的云记录，具体细节为：
- 任何`CloudBlackShare`设置为`1`的骰娘在触发自动拉黑后会通过简单的POST指令对一个设置为`shiki.stringempty.xyz`域名的基于PHP的服务器进行无鉴权的数据上传
- 任何`CloudBlackShare`设置为`1`的骰娘在完成上传后服务器会返回一个值，该值将作为黑名单信息广播广播时的`wid项`（该称呼可能随时间推移发生改变）
- 任何`CloudBlackShare`设置为`1`的骰娘都将经过通过简单的POST指令对一个设置为`shiki.stringempty.xyz`域名的基于PHP的服务器进行黑名单信息的比对验证，如果存在记录且具有云黑效力，则无视发送者权限接受并同步该黑名单。
- 设置为`shiki.stringempty.xyz`域名的基于PHP的服务器曾被发现有严重的SQL注入漏洞，等。
- 经过确认，该功能的设计者——Shiki——认为，终极理想状态的设计应当是：`“是云黑”`与`“具有云的效力”`与`“有wid”`是完全等同的。
- `CloudBlackShare`项默认为`1`
- `CloudBlackShare`项未被收录于`Dice! 2.3.8Exp10(556)`最终的`Master_Manual`与`User_Manual`中。
- `CloudBlackShare`项的缺失最终由本人`仑质`发现并提出，被收录于`Dice! 2.4.0Beta3(563)`的文档中，该更改相关的`Pull requests`由`AzusaYukina`提交，你可以在这里查看：[AzusaYukina - Update Master_Manual.md - 新增了 CloudBlackShare 的解释](https://github.com/Dice-Developer-Team/DiceV2Docs/pull/1)
- `CloudBlackShare`项相关的简单的POST指令对一个设置为`shiki.stringempty.xyz`域名的基于PHP的服务器进行无鉴权的云记录上传更新与验证逻辑已经开源于Github页面，并且由于项目所选的开源协议必须开源。

故而，基于这些细节，`CloudBlackShare`项的默认值被我修改为`0`，且在设置完成时将会发送`strConfSetToUnsafe`的警告。

#### 调整配置项
- `CloudBlackShare`
缺省默认：`0`（原本为`1`）
该项将会决定是否进行云记录的上传与验证。
详见本小节`上传云记录相关调整上传云记录相关调整`部分。

#### 额外配置项
- `BelieveShikiExceptGroup`
缺省默认：`0`
控制是否拉取[http://shiki.stringempty.xyz/DiceCloud/except_group.json](http://shiki.stringempty.xyz/DiceCloud/except_group.json)的ExceptGroup。
当为0时，不拉取。
当为1时，拉取并装载。
完全更改ExceptGroup需要进行应用的重载。
- `BelieveShikiDicelist`
缺省默认：`0`
控制是否拉取[http://shiki.stringempty.xyz/DiceList/](http://shiki.stringempty.xyz/DiceList/)的Dicelist。
当为0时，不拉取。
当为1时，拉取并装载。
完全更改Dicelist需要进行应用的重载。
- `BelieveOlivaDicelist`
缺省默认：`0`
控制是否拉取[http://benzenpenxil.xyz/Oliva-DiceList/](http://benzenpenxil.xyz/Oliva-DiceList/)的Dicelist。
当为0时，不拉取。
当为1时，拉取并装载。
完全更改Dicelist需要进行应用的重载。
- `BelieveThirdDicelist`
缺省默认：`0`
控制是否拉取来自第三方的Dicelist。
当为0时，不拉取。
当为1时，拉取并装载。
该部分暂未完成。

#### 额外自定义回复
- `strConfSetToUnsafe`
缺省默认：`已经切换至存在缺陷的功能！请确保知晓这个操作可能导致的后果！`

### Helpdoc模糊匹配
- 指令：`.help [所查条目]`

基于原版Helpdoc功能进行了加强，在没有对应条目时将进行模糊匹配搜索，搜索与排序算法基于`最长子字符串`与`最小编辑距离`两个算法的组合。

#### 额外自定义回复
- `strHlpRecommend`
缺省默认：`已为您找到以下近似条目：`


### 扩充版今日人品Jrrp
- 指令：`.jrrp`

对原版的jrrp进行了较大扩充，较为复杂。

#### 额外关键词
- `{dashes}`
该关键词在使用指令时将被替换为一个缓冲条，用于展示jrrp的数值大小
- 所有牌堆引用方式`{xxx}`或`{%xxx}`
该关键词在使用指令时将被替换为对应牌堆的抽取结果。

#### 额外配置项
- `LocalJrrp`
缺省默认：`1`
本地Jrrp控制项。
当为0时，关闭本地Jrrp，使用官方版本同样的在线Jrrp生成服务器结果。
当为1时，开启本地Jrrp，本地生成的Jrrp采用散列哈希算法。
当为2时，开启本地Jrrp，本地生成的Jrrp采用散列哈希算法，并使用本机QQ号对算法进行加盐，从而使得结果因骰娘账号变化而不同。
- `LocalJrrpMin`
缺省默认：`1`
本地Jrrp最小值控制项。
*当`LocalJrrp`为0时无效。*
该值将会使得本地Jrrp结果的最小值为其所设置的大小。
- `LocalJrrpRange`
缺省默认：`100`
*当`LocalJrrp`为0时无效。*
该值将会使得本地Jrrp结果范围宽度为其所设置的大小。
结合`LocalJrrpMin`项可以将本地Jrrp出值控制为：`[LocalJrrpMin]`至`[LocalJrrpMin]+[LocalJrrpRange]-1`
- `JrrpDashesRange`
缺省默认：`25`
本地Jrrp`{dashes}`关键词长度控制项。
该值将会使得本地Jrrp结果`{dashes}`关键词宽度为其所设置的大小。


### 暗检定
- 指令：`.rah [技能]`

可以进行暗检定，查看结果需要使用`.ob`指令进入旁观模式，骰娘将会私聊发送结果。

#### 额外自定义回复
- `strHiddenCheck`
缺省默认：`{pc}进行{attr}暗检定`

### 对抗检定
- 指令：`.rav [技能] [@对方]`

可以直接进行对抗检定。


