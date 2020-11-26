## Oliva Dice! 手册

*For 2.5.0CHAOS1*

> *世界是属于每一个人的。要创造一个充满逻辑并尊重每一个人的世界。*    
> *——《Новый Элемент Расселения》A.D.1960 Москва*

![DIXE(OLIVADICE)](_static/DIXE_OLIVADICE.jpg)

### 喧闹测试
欢迎参加喧闹测试，目前该项目正处于第一阶段。

你可以在通过在`DiceXXXXXXXX/plugin/`目录下创建`.lua`脚本文件来增加扩展指令，脚本基本结构如下。

### 文件格式

```lua
command = {};

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

### 基本模块

#### dice模块

dice.draw(`str`)  
dice.send(`str`,`id`,`mode`)  
dice.int2string(`int`)  
dice.rd(`str`)  
dice.md5(`str`)  
