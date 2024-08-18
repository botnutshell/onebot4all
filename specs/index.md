# OneBot4All 标准

OneBot 是一个聊天机器人应用接口标准，旨在统一不同聊天平台上的机器人应用开发接口，使开发者只需编写一次业务逻辑代码即可应用到多种机器人平台。

!!! tip "提示"

    如果本页有看不懂的词汇，请参考 [术语表](glossary.md)。

**OneBot4All 则是对 OneBot V12 的改进，试图使不同平台的实现不再扩展出互不兼容的的特定平台标准，真正实现上述的愿景。**

!!! tip "注意"

    在本文的大多数内容中，OneBot 直接指代 OneBot4All。如同时提及 OneBot4All 与 OneBot V12，将使用全称区分。

## OneBot4All 所更改的内容

如果你已经十分了解 OneBot V12，以下将简单列出本标准与之不同的内容：

### 动作

- [get_support_message_segments](./interface/meta/actions/#get_support_message_segments)

### 消息段

- [message_nodes](./interface/message/segments.md#message_nodes)

## 为什么要有 OneBot4All？

OneBot V12 已经在草案阶段停留了两年以上。在这期间，虽然社区也不断涌现着不同平台的实现与各种语言的 LibOneBot，但加起来却仍比不过 OneBot V11 实现的增量。虽然开发者普遍有维持旧版的惯性，但望着[生态页面](https://onebot.dev/ecosystem.html)上寥寥可数的 6 个实现（其中仍在持续开发的两个同时支持 OneBot V11），想必都会得出这么一个结论——OneBot V12 是个不被社区认可的失败标准。我不是想指责 OneBot V12 的制定者，但这就是 OneBot 身为次世代标准却无法取代旧标准的窘境。

要说其失败在哪，我对此的看法是：OneBot V12 想要抛弃 QQ 平台的包袱而支持更多平台，却因此变得束手束脚，只敢制定所有聊天平台的交集，其余全部交给实现开发者自行决定。这看似是一种民主的放权，实际就是不作为。身为一个想要统一所有聊天平台机器人的标准，实际上却只统一了不同聊天平台之间本来就极为相似的极小部分内容，无异于抛弃了自身的存在意义。而因为不同平台原生命名的不同，想让不同的实现开发者商讨出同一个扩展字段的可能性微乎其微——即使有交流群的存在，大部分人也只是埋头写代码。更现实的情况是：新的实现出现时，旧的实现已经停止开发。这时新的开发者与其去兼容一个本来就没有几个用户的旧实现，不如直接写更符合自己喜好的扩展字段。而这种分裂的现状也导致 OneBot 应用的开发者要针对不同的实现编写不同的代码，那还不如直接用应用框架自己的跨平台适配。

OneBot4All 一开始的想法是抛弃 OneBot V12，将 OneBot V11 扩展成跨平台的标准。但 OneBot V12 确实有很多跨平台的设计，而且应用框架也对其进行了适配，那么或许……该做的只是扩展更多更全的接口定义？不管怎样，维持现状是最糟糕的选择，新的 OneBot 标准必须替代 OneBot V12，那为什么不能是 OneBot4All？

## OneBot 标准是什么？

OneBot 标准是对开发聊天机器人所使用的 API 的一个抽象，是对聊天机器人 API 的通信方式、传输的数据格式和字段等的一个标准化定义。如果将 OneBot 标准类比于 C 语言、ECMAScript、POSIX 标准等，则 OneBot 实现对应 GCC、Chrome V8、Linux 等。

## OneBot 标准不是什么？

OneBot 标准，即本网站上的所有内容，只是一个文档，OneBot 标准本身没有一个中心化的官方实现，而是依赖社区中有兴趣、有能力的开发者们针对各个语言/运行时实现 LibOneBot、基于 LibOneBot 针对各个机器人平台实现 OneBot 标准、基于 OneBot 标准实现各种开发框架。

## 组成部分

OneBot 标准由 OneBot Connect 和接口定义两部分组成：

- OneBot Connect 规定了 OneBot 应用与 OneBot 实现之间通过网络交互所使用的通信方式和数据协议
- 接口定义描述了一组标准事件、动作、消息段和它们的扩展规则

## 文档用词

本文档中的 `必须`（MUST）、`不得`（MUST NOT）、`应`/`应该`（SHALL）、`不应`/`不应该`（SHALL NOT）、`建议`（RECOMMENDED）、`不建议`（NOT RECOMMENDED）、`可以`（MAY）和 `可选`（OPTIONAL）等能愿动词按照 [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) 中的描述进行解释。
