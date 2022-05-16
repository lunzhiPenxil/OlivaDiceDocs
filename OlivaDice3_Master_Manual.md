# OlivaDice For OlivOS 骰主手册

*For Ver.3.1.16(1026)*

> *世界是属于每一个人的。要创造一个充满逻辑并尊重每一个人的世界。*    
> *——《Новый Элемент Расселения》A.D.1960 Москва*

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

### 个性化定制

##### 自定义回复词:
`.str[配置项] [配置值]`  修改对应的自定义配置  
`.str[配置项]`  查看对应的自定义配置  

本核心内置了一套str回复词配置工具，可以通过以上指令进行骰子回复词的配置，例如：  
使用  
`[.strPcSkillCheckFailed 哈哈，失败，哈哈]`  
即可将检定失败回复词进行设置。  

##### 自定义帮助文档
`.helpdoc [帮助名称] [帮助内容]`  设置帮助文档  
`.helpdoc [帮助名称]`  删除帮助文档  