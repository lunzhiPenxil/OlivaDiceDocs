## Json2Yaml for Dice
网上跑团时进行Roll点判定的解决方案中，当前的主流方案是基于酷Q的骰子机器人，其中实现骰值的主流插件为[塔系核心(By SinaNya)](https://sinanya.com/#/)、[Dice!(By 溯洄)](https://kokona.tech/)、[青果Dice(By 仑质)](https://oliva.dicer.wiki/olivadice)、Shiki分支Dice!(By Shiki)、MDice!(By 惠惠)等。    
牌堆功能是各类主流插件中一项可由骰主进行定制的功能，以数据序列化交换格式文件的形式进行编写，其中一部分插件采用了Json格式，而本人所使用的**塔系核心**采用了Yaml格式，因此不同插件的骰主之间进行牌堆内容的交流时出现了数据不互通与重复工作的问题，尽管目前也有Json到Yaml的在线转换器，但往往在一些细节处不尽如人意，转换生成的文件并不能直接被载入使用。    
    
**基于以上情况，本人基于Python实现了一个具有图形交互界面且针对骰子牌堆优化的转换器。**    
    
## 获取工具
请移步[Release页面](https://github.com/lunzhiPenxil/json2yaml-for-dice/releases)。

## 使用手册
### 开始之前
#### 应用场景
以下是本牌堆转换器**可以**做到的：
1. 我想将其它来自核心的Json格式牌堆文件转换为塔系核心可以正常使用的Yaml格式牌堆文件。
2. 我是由其它核心转移而来的骰主，想要完全移植之前所使用的牌堆。
3. 我是牌堆作者，我想为我所编写的牌堆生成一份Yaml格式牌堆文件。

以下是本牌堆转换器**不能**做到的：
1. 我想写一个新牌堆。
2. 我想修改现有牌堆。
3. 我想要将除Json格式以外的牌堆文件转换为塔系核心可以正常使用的Yaml格式牌堆文件。

如果您满足以上条件，那么本牌堆转换器将是一个简便快捷的工具。

#### 有何区别
Json与Yaml都是数据序列化格式，其中塔系核心采用了Yaml格式，Dice系核心的牌堆功能采用了Json格式。
转换器主要针对Dice系牌堆进行优化，故在此以Dicr系牌堆举例。

##### 塔系核心×Yaml
1. 每个牌堆作为一个独立的完整文件。
2. 牌堆文件具有名称、指令、作者、简述等必需项，以及子指令、默认指令等可选项。
3. 抽取指令为`.deck 指令 子指令`。
4. 子项中使用`{$xxx}`表示放回抽取，加`%`表示不放回抽取。
5. 放回抽取没有迭代次数上限，不放回抽取有迭代次数上限。
6. 不同牌堆文件之间不允许进行变量的交叉引用。
7. 原核心不含牌堆，但提供整套牌堆下载途径。

##### Dice系核心×Json
1. 牌堆可以分散为多个文件，不同牌堆之间没有明显界限。
2. 牌堆只有父项与子项，并且不需要在文件中做出其它注明。
3. 抽取指令为`.draw 父项`。
4. 子项中使用加`%`表示放回抽取，使用`{xxx}`表示不放回抽取。
5. 任何抽取都没有迭代次数上限。
6. 不同牌堆文件之间可以随意进行变量的交叉引用。
7. 原核心中硬编码了部分常用牌堆。

#### 如何处理
牌堆转换器将会允许你：
1. 查看想要转换的牌堆的内部结构。
2. 自定义新的牌堆名称与指令。
3. 选择默认指令与子指令。
4. 自动解决牌堆搬运时的各类细节问题。

### 开始使用
#### 获得工具
从Github的Release中获取最新版本：[Json2Yaml for Dice - Release](https://github.com/lunzhiPenxil/json2yaml-for-dice/releases)。   
执行文件的运行应当不需要特殊的环境支持，如果有无法运行的情况请参考`其它`项中的联系方式联系作者沟通。

#### 打开工具
双击执行文件，启动时间可能会长至8秒，但这属于正常现象。
这里以`1.0.8.20200122.1`版本为例：

![界面](/_static/j2y_ui.jpg)

你可以通过菜单栏：`关于 > 关于` 查看版本，如下图：

![关于](/_static/j2y_about.jpg)

#### 进行转换
要进行转换，首先你需要导入原Json文件，单击菜单栏：`文件 > 导入文件` ，将会弹出一个资源浏览器，在其中找到你需要转换的文件。

![导入文件](/_static/j2y_do_import.jpg)

等待进度条走满后，就可以看到该牌堆内的所有父项与子项结构：

![导入后](/_static/j2y_after_import.jpg)

下方输入框为你可以定义的项目，你需要认真填写，这将影响到你对该牌堆的使用过程。

1. 在`名称/指令`项中输入该牌堆的名称，这同时也将是你抽取该牌堆时的指令，对应牌堆文件中的`name`项与`command`项，例如填入`Arknights`，那么抽取该牌堆时的指令就是`.deck Arknights 子指令`。
2. 在`作者`一栏填入原作者，对应牌堆文件中的`author`项，请在搬运前与原作者进行沟通。
3. 在`版本`一栏填入该牌堆版本号，对应牌堆文件中的`version`项，这一项主要用于展示在骰子面板上。
4. 在`描述`一栏填入对于该牌堆的简要描述，对应牌堆文件中的`desc`项，这一项主要用于展示在骰子面板上。
5. 在`子指令`一栏填入子指令并用半角逗号隔开，对应牌堆文件中的`includes`项，例如填入`default,单发,十连`，那么抽取时的指令就可以是`.deck Arknights 十连`等，子指令需与作为子指令的父项一一对应。
6. 在`default`一栏填入默认指令，对应牌堆文件中的`default`项，例如，填入`十连`，那么输入`.deck Arknights`就相当于输入指令`.deck Arknights 十连`，填入的项需与作为子指令的父项对应。

这里以`异想体-脑叶`牌堆（作者：哦哦君）为例，输入各项后如下：

![设置后](/_static/j2y_after_config.jpg)

转换后塔系核心指令与Shiki系核心指令的对应关系将如下：
- `.deck 异想体` <-> `.draw 异想体`
- `.deck 异想体 脑叶装备` <-> `.draw 脑叶装备`

确认一切设置无误后，单击菜单栏：`文件 > 开始转换` ，进行转换，如果转换无误，则会弹出提示框，表示转换成功，一般如图：

![保存](/_static/j2y_save.jpg)

### 进阶使用
以下功能主要是在更复杂的情况下，为了让牌堆转换效果更好所提供的可选项。

#### 右键菜单
本工具的大部分组件都设计了对应的右键菜单功能，灵活运用后，理应能大幅度提高牌堆搬运的效率。

#### 解决依赖项
可以在菜单栏：`操作 > 尝试解决依赖项` 切换该功能的状态，该功能默认开启。
如果牌堆需要交叉引用其它文件的父项，那么在导入Json文件后应会弹出如下对话框：

![需要依赖项](/_static/j2y_dep_need_notice.jpg)

这种情况需要您提供包含了该牌堆所引用项，用过菜单栏：`文件 > 加载依赖项` 进行加载，一次可选择多个文件。
同时，转换器内部也内置了原Shiki系核心所内置的牌堆，如果你不确定所需要的依赖项是否包含在内，可以先尝试直接进行转换，如果直接弹出已保存的对话框则为解决依赖成功。
选择完毕后，确保`操作 > 尝试解决依赖项` 为开启状态，然后选择菜单栏：`文件 > 开始转换` 就可以尝试在转换时自动解决依赖关系。
如果所加载的依赖项未能完全覆盖需要解决的依赖项，那么，将会弹出如下图所示的对话框，列出未能找到的依赖项：

![未解决](/_static/j2y_dep_notice.jpg)

那么你需要找到所依赖的牌堆，并加载它，然后再次尝试转换。

#### 忽略不放回
可以在菜单栏：`操作 > 忽略不放回` 切换该功能的状态，该功能默认关闭。
Shiki系Json牌堆中不放回抽取更加常见，而塔系Yaml牌堆的不放回抽取存在迭代次数上限，并且实际编写中很多作者在大多数使用了多次不放回抽取迭代的部分其实使用放回抽取并无大碍，也存在某些不负责任的作者在编写时乱用错用导致牌堆无法正常使用，所以提供了这项功能。
如果你发现你转换所得的牌堆在抽取时出现了大量`未找到`项目，请开启此项再尝试转换。

#### 版本号优化（该功能已为非必要，已置为默认关闭）
可以在菜单栏：`操作 > 版本号优化` 切换该功能的状态，该功能默认关闭。
Shiki系Json牌堆并不需要版本信息，但是由于大部分作者持续更新自己的牌堆，版本序号比较混乱，塔系Yaml牌堆要求填写版本号，并且版本号必须为整数，不可以有小数点，否则会导致骰子无法正常启动，开启此项可以帮助你处理掉版本号中不符合要求的部分。

#### 排版格式优化（该功能已为非必要，已置为默认关闭）
可以在菜单栏：`操作 > 排版格式优化` 切换该功能的状态，该功能默认关闭。
塔系Yaml牌堆的抽取项在生成回复文本时会添加一个半角空格，但是对于每个父项的第一个子项会忽略这个步骤，这个特性有时会造成排版混乱，开启这个选项可以帮助你处理这个问题。

#### 添加Info项
可以在菜单栏：`操作 > 添加Info项` 切换该功能的状态，该功能默认开启。
该功能将在牌堆中添加一个`Info`项，此项可以通过发送`.deck 指令 info`进行查看，将标注原作者与牌堆转换器的版本。

## 项目主页
[json2yaml-for-dice - 一个针对骰子牌堆优化的转换器](http://benzenpenxil.xyz/json2yaml-for-dice/)

## 宣传
本人的定制化骰娘小青果酱：[仑质/青果 - 依旧存在于此](http://benzenpenxil.xyz/oliva-still-here/)

## 其它
本牌堆转换器由仑质(BenzenPenxil)基于Python独立开发，在使用上遇到技术问题请加作者的群`青果批发车间(828786809)`进行沟通，或在项目的Github页面提交Issues。   
![群二维码](/_static/j2y_group.jpg)

## 更新日志      
	2020/06/05：[+] 针对新版塔系核心将调整初始化配置，关闭了版本号和排版格式优化
	2020/06/05：[+] 将Python版本切换为3.8.3
	2020/01/22：[-] 解决了第二次转换时依赖项无效的bug
	2020/01/21：[+] 添加了从文件加载依赖项的功能（重要）
	2020/01/21：[+] 添加了作者信息项开关
	2020/01/20：[+] 添加了排版格式优化模式
	2020/01/20：[+] 添加了版本号优化模式
	2020/01/19：[+] 优化了牌堆内骰值功能
	2020/01/19：[+] 添加了忽略不放回模式
	2020/01/19：[+] 添加了纵向滚动条
	2020/01/17：[+] 增加了右键菜单
	2020/01/17：[+] 增加了操作栏功能
	2020/01/17：[+] 增加了项目主页的入口
	2020/01/17：[+] 增加了进度条
	2020/01/17：[+] 增加了对于emoji的支持
	2020/01/16：[+] 将输入栏的默认信息设置为简单引导
	2020/01/16：[+] 将交互按钮集成至新增的菜单栏
	2020/01/16：[+] 增加了简单的导入文件查错功能
	2020/01/15：[+] 对部分复用代码进行重构
	2020/01/15：[+] 实现进程图标嵌入
	2020/01/14：[+] 实现基本转换功能