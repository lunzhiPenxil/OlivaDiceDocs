# Json5快速入门

`Json5`是流行的`Json`文件格式的扩展，旨在更易于手动编写和维护（例如配置文件），想要理解它，你应当首先已经阅读过[Json快速入门](/JsonHelp)，并已经基本了解了原版`Json`。  
特别需要注意的是，它不适用于机器对机器的通信，因为在机器与机器的交互领域中，规则更加简洁且严格的原版`Json`更为合适。  

**相比原版简洁的`Json`，`Json5`为了具有可读性，设置了相当多听起来很繁琐的设计但是用起来很顺手的设计，所以在这里，我不会完整的介绍`Json5`的规则，而是只会简单的提到一些在使用过程中比较常见的新特性**  

## 关键的特性介绍

### 注释
支持以`//`开头的单行注释，以及以`/*`和`*/`包裹的多行注释（格式基本类似`C`语言）。  

```json5
[
    114514,
    "哼哼啊啊啊啊",
    [
        "好臭啊"
    ],
    {
        "真的太臭了": "真的" //确实
    }
    /*
      这些真的
      确实
      太臭了
    */
]
```

### 多余尾随逗号
对象和数组的最后一个条目可以允许多余的尾随逗号。  

对象：  
```json5
{
    "key1": "value1",
    "key2": "value2",
    "key3": "value3",
    "key4": "value4",  //注意此处
}
```

数组：  
```json5
[
    "value1",
    "value2",
    "value3",
    "value4",  //注意此处
]
```

### 转义符换行
字符串中可以在换行前采用转义符`\`来使字符串跨越多行，而无需写抽象的`\n`换行符。  
```json5
[
    "value1",
    "val\
换行\
换了很多行\
ue2",
    "value3",
    "value4"
]
```
这相当于原版`Json`的
```json
[
    "value1",
    "val\n换行\n换了很多行\nue2",
    "value3",
    "value4"
]
```

## 完整的特性介绍
`Json` 不支持的以下 [ECMAScript 5.1](https://262.ecma-international.org/5.1/) 功能已扩展到 `Json5`。  

### 对象
- 对象键可以是 [ECMAScript 5.1 IdentifierName](https://262.ecma-international.org/5.1/#sec-7.6)。
- 对象可能有一个尾随逗号。

### 数组
- 数组可能有一个尾随逗号。

### 字符串
- 字符串可以用单引号引起来。
- 通过转义新行字符，字符串可以跨越多行。
- 字符串可能包含字符转义。

### 数字
- 数字可以是十六进制的。
- 数字可能有前导或尾随小数点。
- 数字可以是 [IEEE 754](http://ieeexplore.ieee.org/servlet/opac?punumber=4610933) 正无穷大、负无穷大和 NaN。
- 数字可能以明确的加号开头。

### 评论
- 允许单行和多行注释。

### 白色空间
- 允许使用额外的空白字符。

### 厨房水槽示例
```json5
{
    // comments
    unquoted: 'and you can quote me on that',
    singleQuotes: 'I can use "double quotes" here',
    lineBreaks: "Look, Mom! \
No \\n's!",
    hexadecimal: 0xdecaf,
    leadingDecimalPoint: .8675309, andTrailing: 8675309.,
    positiveSign: +1,
    trailingComma: 'in objects', andIn: ['arrays',],
    "backwardsCompatible": "with JSON",
}
```
