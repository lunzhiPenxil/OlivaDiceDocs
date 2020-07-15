## Json2Yaml for Dice
网上跑团时进行Roll点判定的解决方案中，当前的主流方案是基于酷Q的骰子机器人，其中实现骰值的主流插件为[塔系核心(By SinaNya)](https://sinanya.com/#/)、[Dice!(By 溯洄)](https://kokona.tech/)、[Shiki系Dice!(By Shiki)](https://github.com/w4123/Dice/tree/Shiki)、MDice!(By 惠惠)等。    
牌堆功能是各类主流插件中一项可由骰主进行定制的功能，以数据序列化交换格式文件的形式进行编写，其中一部分插件采用了Json格式，而本人所使用的**塔系核心**采用了Yaml格式，因此不同插件的骰主之间进行牌堆内容的交流时出现了数据不互通与重复工作的问题，尽管目前也有Json到Yaml的在线转换器，但往往在一些细节处不尽如人意，转换生成的文件并不能直接被载入使用。    
    
**基于以上情况，本人基于Python实现了一个具有图形交互界面且针对骰子牌堆优化的转换器。**    
    
## 获取工具
请移步[Release页面](https://github.com/lunzhiPenxil/json2yaml-for-dice/releases)。

## 项目主页
[json2yaml-for-dice - 一个针对骰子牌堆优化的转换器](http://benzenpenxil.xyz/json2yaml-for-dice/)

## 宣传
本人的定制化骰娘小青果酱：[仑质/青果 - 依旧存在于此](http://benzenpenxil.xyz/oliva-still-here/)

## 其它
本牌堆转换器由仑质(BenzenPenxil)基于Python独立开发，在使用上遇到技术问题请加作者的群`青果批发车间(828786809)`进行沟通，或在项目的Github页面提交Issues。   
![群二维码](_static/j2y_group.jpg)