## OlivaDice 喧闹手册

*For 2.5.0CHAOS1*

> *世界是属于每一个人的。要创造一个充满逻辑并尊重每一个人的世界。*    
> *——《Новый Элемент Расселения》A.D.1960 Москва*

![DIXE(OLIVADICE)](_static/DIXE_OLIVADICE.jpg)

### 喧闹测试
欢迎参加喧闹测试，目前该项目正处于第一阶段。

你可以在通过在`DiceXXXXXXXX/plugin/`目录下创建`.lua`脚本文件来增加扩展指令，脚本基本结构如下。

### 文件格式范例

```lua
command = {}

function duel(Msg)
    a1 = dice.rd("1d100")
    a2 = dice.rd("1d100")
    a3 = dice.rd("1d100")
    a4 = dice.rd("1d100")
    a5 = dice.rd("1d100")
    b1 = dice.rd("1d100")
    b2 = dice.rd("1d100")
    b3 = dice.rd("1d100")
    b4 = dice.rd("1d100")
    b5 = dice.rd("1d100")
    rv = ""
    rv = rv .."决斗A:\n"
    rv = rv .. dice.int2string(a1) .. " + "
    rv = rv .. dice.int2string(a2) .. " + "
    rv = rv .. dice.int2string(a3) .. " + "
    rv = rv .. dice.int2string(a4) .. " + "
    rv = rv .. dice.int2string(a5) .. "\n= "
    A = a1 + a2 + a3 + a4 + a5
    rv = rv .. dice.int2string(A)
    rv = rv .."\n决斗B:\n"
    rv = rv .. dice.int2string(b1) .. " + "
    rv = rv .. dice.int2string(b2) .. " + "
    rv = rv .. dice.int2string(b3) .. " + "
    rv = rv .. dice.int2string(b4) .. " + "
    rv = rv .. dice.int2string(b5) .. "\n= "
    B = b1 + b2 + b3 + b4 + b5
    rv = rv .. dice.int2string(B)
    rv = rv .. "\n"
    if(A > B)
    then
        rv = rv .. "A胜"
    elseif(A < B)
    then
        rv = rv .. "B胜"
    else
        rv = rv .. "此乃平局"
    end
    return rv
end

command["(\\.|。)duel"] = "duel"
```

### 脚本原型

对于如下脚本原型:  
```lua
command = {}

function temFunc(Msg)
    Reply = ""
    return Reply
end

command[Regex] = Func
```

#### 指令映射

对于如下指令映射原型:  
```lua
command[Regex] = Func
```

| 变量名称     | 数据类型     | 说明                 | 缺省          |
|:------------|:-----------|:---------------------|:-------------|
| command     | table      | 用于暴露指令的映射表     | 此为必须项    |
| Regex       | string     | 设置指令的正则表达式     | 此为必须项    |
| Func        | string     | 指令对应所映射的函数名称  | 此为必须项    |

可以实现对于`Regex`正则表达式匹配后的指令，运行`Func`函数。

#### 传入参数

对于如下函数原型:  
```lua
function temFunc(Msg)
```

`Msg`将会传入一个结构体，你可以如此调用它的成员:  
```lua
Msg.fromGroup
Msg.str[1]
```
它将有以下成员:  

| 成员名称     | 数据类型     | 说明                                                  |
|:------------|:-----------|:------------------------------------------------------|
| msg         | string     | 所匹配的回复全文                                         |
| str         | table      | 正则表达式的子表达式                                      |
| str_max     | integer    | 子表达式数量+1                                           |
| msgType     | integer    | 消息类型，0为私聊，1为群聊                                 |
| selfId      | integer    | 本机QQ                                                  |
| fromQQ      | integer    | 本条消息发送者QQ                                          |
| fromGroup   | integer    | 本条消息所在群号                                          |
| tergetId    | integer    | 如果为私聊则为本条消息发送者QQ，否则为本条消息所在群号          |
| fromQQTrust | integer    | 本条消息发送者的信任度                                     |
| fromQQInfo  | integer    | 本条消息发送者的群内权限，0为私聊，1为群员，2为管理，3为群主     |

### 内置模块

结合现有功能提供以下内置模块以便于扩展指令的程序设计直接对本体进行干预。

#### dice模块

---  
- **draw**  
```lua
rv = dice.draw(msg)
```

| 形参名称     | 数据类型     | 说明                    | 缺省          |
|:------------|:-----------|:------------------------|:-------------|
| msg         | string      | 你所需要进行转换的消息     |              |

| 返回值名称    | 数据类型     | 说明                    | 缺省          |
|:------------|:-----------|:------------------------|:-------------|
| rv          | string      | 返回经过抽牌堆处理后的结果  |              |

将`msg`经过抽牌堆处理后作为返回值传出。

---  
- **send**  
```lua
dice.send(`msg`,`tergetId`,`msgType`)
```

| 形参名称     | 数据类型     | 说明                                    | 缺省          |
|:------------|:-----------|:----------------------------------------|:-------------|
| msg         | string      | 你所需要发送的消息                        |              |
| tergetId    | integer     | 目标id，可以是QQ或群号，需结合`msgType`     |              |
| msgType     | integer     | 消息类型，0为私聊，1为群聊                 |              |

*本函数无返回值。*  
实现发送消息。  

---  
- **int2string**  
```lua
rv = dice.int2string(str)
```

| 形参名称     | 数据类型     | 说明                    | 缺省          |
|:------------|:-----------|:------------------------|:-------------|
| str         | string      | 记录了某个整数的字符串     |              |

| 返回值名称    | 数据类型     | 说明                    | 缺省          |
|:------------|:-----------|:------------------------|:-------------|
| rv          | integer    | 转换完成后的数值           | 0            |

将字符串转换为数字。

dice.rd(`msg`)  
dice.md5(`msg`)  
dice.DiceDir()  
dice.mkDir(`path`)  
dice.GBKtoUTF8(`str`)  
dice.UTF8toGBK(`str`)  
dice.UrlEncode(`str`)  
dice.UrlDecode(`str`)  
dice.getPcSkill(`QQ`,`Group`,`Skill`)  
dice.setPcSkill(`QQ`,`Group`,`Skill`,`Skill_Val`)  
dice.getPcName(`QQ`,`Group`)  
dice.setPcName(`QQ`,`Group`,`New_Name`)  
dice.fReadJson(`file`,`json_obj`,`json_obj`,`json_obj`,...)  
dice.fGetJson(`file`,`default`,`json_obj`,`json_obj`,`json_obj`,...)  
dice.fSetJson(`file`,`new_value`,`json_obj`,`json_obj`,`json_obj`,...)  
dice.fDownWebPage(`url`,`file`)  
