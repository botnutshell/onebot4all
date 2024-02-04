# OneBot4All

**OneBot** 是一个聊天机器人应用接口标准，旨在统一不同聊天平台上的机器人应用开发接口，使开发者只需编写一次业务逻辑代码即可应用到多种机器人平台。

**注意，本仓库是 [nonebot-plugin-all4one](https://github.com/nonepkg/plugin-all4one) 所用的 OneBot4All 标准，要查看官方的 OneBot 标准，请前往 [botuniverse/onebot](https://github.com/botuniverse/onebot)。**

*关于简称：请使用 **ob4a** 或者 **140**。*

## 特点

- **繁杂**：标准所描述的连接规范和接口定义繁杂琐碎，难于理解、实现和接入，同时文档语言模棱两可。
- **特化**：接口定义首先为 Telegram Bot API 和 OneBot V11 设计，再考虑兼容其余聊天机器人平台。
- **死板**：针对不同聊天机器人平台提供的特色功能，接口定义中不存在的，OneBot4All 实现不应理会。
- **封闭**：标准的制定和维护采用黑箱模式，OneBot4All 实现开发者提出建议，看我心情决定是否接收。

## 本地预览

要在本地预览 OneBot4All 标准文档，请参考下面命令：

```sh
$ pip install -r requirements.txt
$ mkdocs serve
```

## 贡献

> 如果你有兴趣帮助完善 OneBot，可积极参与 [discussions](https://github.com/botuniverse/onebot/discussions) 中的讨论、提出 RFC 或帮助更新标准文档，具体贡献方式请参考 [贡献指南](https://github.com/botuniverse/onebot/blob/main/CONTRIBUTING.md)。

*以上不是我没改链接，就是让你去贡献官方的 OneBot V12。*

*至于我这里，直接提 Issue 即可，但首先你得是个实现（官方标准的实现亦可）开发者。*
