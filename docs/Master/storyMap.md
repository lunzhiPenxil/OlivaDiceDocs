# OlivaStory For OlivOS 自定义故事路线图编写指南

*For Ver.3.3.24(1074)*  

> *世界是属于每一个人的。要创造一个充满逻辑并尊重每一个人的世界。*    
> *——《[Новый Элемент Расселения](https://ru.wikipedia.org/wiki/%D0%9D%D0%BE%D0%B2%D1%8B%D0%B9_%D1%8D%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82_%D1%80%D0%B0%D1%81%D1%81%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F)》A.D.1960 Москва*


## 开始使用
`OlivaStoryCore`是在`OlivaDice`的`3.3.24`版本中同步发布的新一代文游引擎，它的设计初衷是为了让骰主能够更加方便地进行文游的设计，以文游的方式进行带团，以及游玩一些类似`向火独行`的文游，为骰主提供了更多的自由度。  
该模块需要加载一种`故事路线图`扩展文件，这种文件通常使用`Json`或者`Json5`编写。  

## 故事路线图
一个简单的故事路线图的文件格式如下  

```json
{
    {
        "name": "故事名称",
        "author": "lunzhiPenxil",
        "version": "1.0.0",
        "svn": 1,
        "ingress": "1",
        "description": "故事描述",
        "story": [
            {
                "flag": "1",
                "text": "节点故事描述",
                "type": null,  // 节点类型，null为普通节点，没有此项时默认为null
                "selection": [
                    {
                        "text": "选项1",
                        "toType": "jump",
                        "to": "2"
                    },
                    {
                        "text": "选项2",
                        "toType": "jump",
                        "to": "3",
                        "hideFlag": "知晓秘密"  // 隐藏选项条件
                    }

                    // ...  各个选项
                ]
            }

            // ...  各个故事节点
        ]
    }
}
```

### 基本信息
可以看到，故事路线图文件是一个`object`，主要由两部分组成：`故事信息`和`故事节点`，其中除了`story`以外的内容都是`故事信息`，具体对照如下：  

名称|类型|说明
:--|:--|:--
name|string|故事名称
author|string|作者
version|string|版本号
svn|number|svn版本号<br/>一个递增的整数版本号<br/>用于识别更新递进关系
ingress|string|入口节点<br/>开始故事时将会从这个节点开始<br/>对应节点的`flag`
description|string|故事描述
story|array|故事节点<br/>详情请看后文

### 故事节点
`story`是一个`array`，里面包含了所有的`故事节点`，每一个故事节点都是一个`object`，其中有如下：

名称|类型|说明
:--|:--|:--
flag|string|节点标识<br/>用于标识该节点<br/>它应当在众多节点之间保持唯一<br/>PS: 在`selection`中使用`toType:jump`时，`to`的值就是这个
text|string|节点故事描述
type|string|节点类型<br/>默认为`null`，`null`为普通节点<br/>其它值请看后文
selection|array|节点选项<br/>详情请看后文

### 节点选项
`selection`是一个`array`，里面包含了所有的`节点选项`，每一个节点选项都是一个`object`，其中有如下：

名称|类型|说明
:--|:--|:--
text|string|选项描述
toType|string|选项跳转类型<br/>目前仅有`jump`，为跳转到指定节点
to|string|选项跳转目标<br/>当`toType`为`jump`时有效，表示选择该选项时跳转到的下一个节点
