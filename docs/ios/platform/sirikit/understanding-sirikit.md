---
title: 了解 SiriKit 概念
description: 本文档介绍在 Xamarin.iOS 应用程序中使用 SiriKit 所需的关键概念。 例如，它讨论了 Intents 和 Intents UI 扩展，SiriKit 权限设计更完美的体验，和的详细信息。
ms.prod: xamarin
ms.assetid: 99EC5C1E-484F-4371-8555-58C9F60DE37F
ms.technology: xamarin-ios
author: lobrien
ms.author: laobri
ms.date: 05/02/2017
ms.openlocfilehash: b2a9e757e8a3407bbb19ae0580e5788eabe84cf0
ms.sourcegitcommit: 4b402d1c508fa84e4fc3171a6e43b811323948fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61188889"
---
# <a name="understanding-sirikit-concepts"></a>了解 SiriKit 概念

_本文介绍如何将需要在 Xamarin.iOS 应用程序中使用 SiriKit 的关键概念。_


新 ios 10、 通过 SiriKit，Xamarin.iOS 应用程序提供的 iOS 设备上使用 Siri 和 Maps 应用的用户可以访问的服务。 此功能提供一个或多个应用扩展中使用新**意向**并**Intents UI**框架。

通过 SiriKit，iOS 应用程序提供服务可供用户使用应用扩展和新的 iOS 设备上使用 Siri 和 Maps 应用访问**意向**并**Intents UI**框架。

使用 Siri 适用于这一概念**域**，组知道相关的任务的操作。 该应用程序可以使用 Siri 与每个交互必须按如下所示划分为其已知的服务域之一：

- 音频或视频呼叫。
- 预订滑水感觉的时间。
- 管理锻炼。
- 消息传递。
- 正在搜索照片。
- 发送或接收付款。

当用户发出的 Siri 请求涉及应用扩展的服务之一时，SiriKit 发送该扩展**意向**对象，描述用户的请求和任何支持的数据。 然后，应用扩展生成的相应**响应**对象的给定**意向**，详细介绍如何扩展可以处理该请求。

## <a name="the-intents-and-intents-ui-extensions"></a>Intents 和 Intents UI 扩展

使用 Siri 和 Maps 应用与通过两种不同类型的应用程序扩展的应用程序的服务进行交互：

- **Intents 扩展**-提供使用 Siri 和 Maps 与该应用程序的内容并执行任务要求履行任何受支持的意图。
- **Intents UI 扩展**-提供用于使用 Siri 或地图内的应用程序的内容将显示自定义 UI。

应用程序必须提供要支持 SiriKit 的 Intents 扩展，它负责提供 Siri 和 Maps 可以向用户显示的信息并处理意向。

创建 Intents UI 扩展是可选的因为 Siri 通常处理所有用户交互，并具有标准的内置 UI 来显示每个受支持的域中的信息。 通过提供 Intents UI 扩展，该应用程序可以使用**意向 UI**框架提供丰富的自定义用户界面提供应用程序的品牌和其他信息。

## <a name="siri-and-the-maps-app-role"></a>使用 Siri 和 Maps 应用角色

用户的语音的请求是语言处理和语义上分析 Siri 可将这些请求转换可操作的意图，意图扩展可以处理的。

映射使用应用程序的意向扩展插件对用户的操作的响应中的映射界面中显示的信息。 如附近的餐馆请求或获取应用的餐馆评审。

使用 Siri 和 Maps 管理所有用户的交互并显示结果使用标准系统接口。 应用程序扩展角色主要是为了提供获取显示的数据。 （可选） 该应用提供 Intents UI 扩展并提供用于增强默认系统接口的自定义 UI。

## <a name="interacting-with-siri-via-sirikit"></a>与通过 SiriKit Siri 交互

本部分将介绍如何通过 SiriKit，用户与使用 Siri 对应用进行交互的概述。 对于此示例中，我们将使用假 MonkeyChat 应用：

[![](understanding-sirikit-images/monkeychat01.png "MonkeyChat 图标")](understanding-sirikit-images/monkeychat01.png#lightbox)

MonkeyChat 保持其自己书联系人的用户的好友名单，但每个屏幕名称 （如 Bobo 示例)，与相关联，并允许用户通过其屏幕名称发送到每个朋友的文本聊天。

有许多用户可能会启动与应用程序中，进行交互，因为不同的人可能会使许多不同的窗体中的同一请求的方法。

例如，如果用户想要将消息发送到 Bobo 其朋友，他们可以使用 Siri 在以下对话：

_用户：您好 Siri MonkeyChat 消息发送。_<br />
_使用 Siri:向其？_<br />
_用户：Bobo._<br />
_使用 Siri:你想要向 Bobo 说出？_<br />
_用户：请发送多个香蕉。_<br />

另一个人可能会使不同的会话使用相同的请求：

_用户：将消息发送到 Bobo MonkeyChat 上。_<br />
_使用 Siri:你想要向 Bobo 说出？_<br />
_用户：请发送多个香蕉。_<br />

和另一个用户可能会进行更短的请求：

_用户：MonkeyChat Bobo 请发送多个香蕉。_<br />
_使用 Siri:好了，发送消息请发送多个香蕉到 Bobo Monkeychat 上。_<br />

或者，甚至在不同的语言进行相同的请求：

_用户：MonkeyChat Bobo s'il vous plaît envoyer plus de bananes。_<br />
_使用 Siri:Oui、 envoi 消息 s'il vous plaît envoyer 以及 de bananes-> Bobo sur Monkeychat。_<br />

尚未另一个用户可能会变得非常冗长其会话中：

_用户：您好 Siri 能够请帮个忙呗并启动 MonkeyChat 应用发送的消息文本请发送多个香蕉。_<br />
_使用 Siri:向其？_<br />
_用户：我最佳 pal Bobo。_<br />

此外，还有许多 Siri 可能响应请求，一些基于如何发出请求的方式：

- **通过按住主页按钮**-Siri 将提供更多 visual 有限口头反馈响应。
- **通过"您好 Siri"** -Siri 将更口头并提供较少 visual 响应。

使用 Siri 也进行调整以满足用户的可访问性需求和将进行交互，并根据这些需求做出响应。

无论如何发出请求时使用 Siri 到请求的响应方式，使用 Siri 处理与用户会话并 （通过其扩展） 应用程序提供的功能。

当用户发出的 Siri 口头请求时，这些是 Siri 将遵循的步骤：

[![](understanding-sirikit-images/monkeychat02.png "使用 Siri 将遵循的步骤")](understanding-sirikit-images/monkeychat02.png#lightbox)

1. 首先，使用 Siri 采用的用户的音频**语音**并将其转换成文本。
2. 接下来，文本将转换成**意向**、 结构化用户的请求的表示形式。
3. 基于意向，将需要使用 Siri**操作**执行用户的请求。
4. 最后，将显示 Siri**响应**（visual 和口头） 向用户根据所执行的操作。

有三种应用程序可以参与 Siri 使用用户的会话的主要方式：

[![](understanding-sirikit-images/monkeychat03.png "三种主要方式，应用程序可以参与用户会话并使用 Siri")](understanding-sirikit-images/monkeychat03.png#lightbox)

1. **词汇**-这是应用程序如何告知 Siri 它需要知道与之交互的单词。
2. **应用程序逻辑**-这些是操作和应用程序需要较长的响应根据给定的意图。
3. **用户界面**-这是应用程序可以为其响应中提供的可选的自定义用户界面。

### <a name="example"></a>示例

给定上述信息后，检查以下会话将如何与 MonkeyChat 应用进行交互：

_用户：您好 Siri 向 Bobo MonkeyChat 上发送消息。_<br />
_使用 Siri:你想要向 Bobo 说出？_<br />
_用户：请发送多个香蕉。_<br />

应用程序需要在会话中的第一个角色是帮助了解用户的语音的 Siri:

[![](understanding-sirikit-images/monkeychat04.png "帮助了解用户语音 Siri")](understanding-sirikit-images/monkeychat04.png#lightbox)

Siri 不具有名称"Bobo"在其数据库中，但该应用程序并不具有与通过其词汇 Siri 共享此信息。 应用还可帮助使用 Siri 认识 Bobo 是接收方，因为它指定其作为 siri*联系人*。

使用 Siri 知道的详细信息，则需要发送比只是接收方，一条消息，因此它将快速检查应用程序扩展名来确定消息是否需要内容。 原因是 MonkeyChat，Siri 将会询问用户响应：*"要说到 Bobo？"*

在上面的示例中，用户已做出响应， *"请发送多个 bananas"*，其中使用 Siri 将绑定到一种结构化**意向**:

[![](understanding-sirikit-images/monkeychat05.png "使用 Siri 将绑定到结构化目的的用户的响应")](understanding-sirikit-images/monkeychat05.png#lightbox)

结构化的目的将包含以下信息：

- **域：** 消息
- **目的：** sendMessage
- **收件人：** Bobo
- **内容：** 请发送多个香蕉

每个域都以组形式知道*操作*零到多个参数可能包括在意图中，可以在其中执行和基于域和操作，发送到应用。

其目的是然后发送到适用于的应用程序扩展处理中。 作为结果的处理目的，应用将生成**IntentResponse**它将被捆绑与意图并包括参数描述应用程序意向的一样。

此外将包括每个 IntentResponse**响应代码**以通知应用程序是否能够完成请求，或不使用 Siri。 某些域具有非常特定的错误响应代码，也可以发送。

最后，将包括 IntentResponse `NSUserActivity` （如那些用来支持手动关闭）。 `NSUserActivity`将用于启动该应用程序，如果响应将要求他们保持 Siri 环境，然后输入应用程序以完成它。 

使用 Siri 将自动生成相应`NSUserActivity`以启动应用，并提取用户离开的位置使用 Siri 环境中。 但是，应用程序可提供其自己`NSUserActivity`与自定义的信息，如有必要。

应用处理目的，并返回到 Siri 响应后，然后将其提供结果向用户 （口头和直观地）：

[![](understanding-sirikit-images/monkeychat06.png "同时口头和直观地向用户显示的结果")](understanding-sirikit-images/monkeychat06.png#lightbox)

使用 Siri 应用可用的域的每个都有几个内置响应用户界面。 但是，由于 MonkeyChat 提供了可选的意向 UI 扩展，它用于向上面的示例中的用户会话的结果。

## <a name="the-intent-lifecycle"></a>意向的生命周期

有三个应用扩展需要面对的 Intents 时要执行的主要任务：

[![](understanding-sirikit-images/monkeychat07.png "意向的生命周期")](understanding-sirikit-images/monkeychat07.png#lightbox)

1. 应用必须**解决**事件上的每个参数。 因此，应用将直到应用程序和用户正在请求的内容达成上相同的参数中调用解析多次 （每一次每个参数），并有时多次。
2. 应用必须**确认**它可以处理请求的意向和 Siri 告诉预期的结果。
3. 最后，应用必须**处理**意图和执行的步骤来实现请求的效果。

### <a name="the-resolve-stage"></a>解析阶段

解析阶段可帮助了解用户已提供，并确保用户实际上意味着应用程序处理意向时，会发生什么情况的值时使用 Siri。 

此阶段还提供了应用程序以与用户会话期间影响 Siri 的行为的机会。 若要执行此操作，该应用将提供**解析响应**。 有多种不同类型的数据使用 Siri 能够理解的预定义响应。

从应用的解决方法响应将是最常见**成功**，这意味着应用到一条信息它了解从参数 （如用户屏幕名称） 匹配特定的数据片段。

可能有的时间时，应用需要确认某个给定的请求匹配的正确条就有关的信息。 在这些情况下，它将发送**ConfirmationRequired**响应如提出 yes 或 no 问题对用户 *"发送消息到 Bobo 很好？"*

可能有其他情况下，应用程序需要用户从中选择选项的简短列表。 在这种情况下，应用将提供**消除二义性**响应，其中用户可以选择从如两到十个选项的列表包含： 

```csharp
Who do you want to message?

* Bobo the Great
* Bobo Jr.
* Little Bobo
```

使用 Siri 将处理执行所选内容，口头或通过使用 Siri UI 交互的用户和结果将发送回应用程序。

在其他情况下，可能没有足够的信息的应用程序来解决该参数或可能有太多匹配项，若要解决使用消除歧义 （如其名称中具有 Bobo 80 用户）。 在此情况下，应用将发送**NeedsMoreDetails**响应和 Siri 会提示用户使其更具体。

如果用户未提供一个值，需要为其处理意向，它可以发送**NeedsValue**响应具有 Siri 提示用户输入值。

如果应用程序不支持特定的参数提供给用户，具有一个值，它可以发送**UnsupportedWithReason**响应，以提供相应原因，为什么不支持的值。 使用 Siri 随后会提示用户输入一个全新的值并给定其原因它是必填项。

最后使用**NotRequired**响应，告知 Siri 应用不要求为给定参数的值。 如果用户仍要提供一个，Siri 将只是被忽略。

### <a name="the-confirm-stage"></a>在确认阶段

在确认阶段有两个用途：

- 若要告知 Siri 处理意向，以便使用 Siri 可以判断用户将要发生的预期的结果。
- 提供机会检查该应用程序可能需要完成由用户，如银行进行请求的付款中具有足够的资金请求的任何所需的状态。

应用程序将提供**意向响应**确认步骤中，应填充了如多应用程序的信息有可用的因此 Siri 可以它有效地进行通信的用户。

根据域和操作类型，使用 Siri 可能会提示用户进行确认，如之前发送付款或预订滑水感觉的时间。

### <a name="the-handle-stage"></a>句柄阶段

处理阶段是使用意向，因为它是应用程序通过执行已要求其执行操作的任务满足用户的请求的位置的点的最重要的部分。

就像它未在确认阶段中，应用将需要提供尽可能多的信息与结果有关的可能的因此使用 Siri 可以与此用户。 有时将直观地显示此信息或在其他时候，Siri 将只返回给用户说出它。 

可能是时间，当应用程序可能需要额外的时间来处理给定的请求，如网络调用延迟或实时人需要满足 （例如完成和发货订单或驾驶汽车到用户的位置） 的请求。 使用 Siri 正在等待从应用程序返回的响应，它将显示等待 UI 向用户告知应用程序处理请求。

理想情况下，应用程序应提供响应 Siri 两到三秒内最多。 如果应用已知道给定的响应要需要更长的过程，它需要发送**InProgress** siri 响应代码。 使用 Siri 随后会告知用户的应用正在处理在后台中的请求，并将继续为此，即使他们离开 Siri 环境。

## <a name="adding-sirikit-to-the-app"></a>向应用添加 SiriKit

与在 iOS 10 SiriKit，Apple 已创建两个新的扩展点：

- **Intents 扩展**-Siri 提供应用程序的内容，并执行完成任何受支持的意向所需的任务。
- **Intents UI 扩展**-提供用于使用 Siri 的应用程序内容将显示自定义 UI。 

也是一个 API，用于向 Siri 以帮助识别中的窗体中提供的字词和短语：

- **应用词汇**的单词和短语所共有的应用程序的每个用户。
- **用户词汇**的单词和短语所独有的给定应用程序用户的。

## <a name="the-intents-extension"></a>Intents 扩展

Intents 扩展负责处理应用程序和 Siri 之间的主要交互操作，如下所示：

[![](understanding-sirikit-images/intents01.png "Intents 扩展")](understanding-sirikit-images/intents01.png#lightbox)

意向扩展可以支持一个或多个意向，它是由开发人员决定他们想要在应用中实现 SiriKit。 开发人员也可以添加单独的意向扩展无需处理每个意向。  也就是说，Apple 请求开发人员限制的意向扩展名的数量，以便使用 Siri 不会有多个进程打开的应用程序中，这需要更多的内存和时间来处理。

开发人员还应注意 Siri 处于活动状态时意向扩展，将在后台运行。 这允许使用 Siri 上与用户的会话仍要处理有关请求的信息的扩展插件与通信时主动执行。

## <a name="privacy-and-security-considerations"></a>隐私和安全注意事项

Apple 已采取了很好的措施，确保专用信息安全时使用 Siri 并且在这种情况下，有几个要求用户在 iOS 设备中记录的交互用户。 例如，当请求滑水感觉的时间或进行付款。

此外，还有一些应用程序可能想要限制用户登录到设备的特定行为。 对于这些情况下，应用程序可以请求**锁定时限制**行为。 这是通过中的设置`Info.plist`文件。

本地身份验证框架是可用于目的扩展应用程序可以向用户请求额外的身份验证信息，因此即使设备已被解锁。

最后，Apple Pay 是可用于目的扩展的因此应用可以完成事务使用 Apple Pay 和 Apple Pay 的内置工作表上使用 Siri 界面的显示。

此外，希望确保用户知道他们何时发送信息到第三方应用并在这种情况下，用户 Apple**必须**时说出的特定名称 （在应用的捆绑包显示名称中指定） 的应用程序发出请求。

Apple 已设计 Siri 执行自然、 流畅会话具有的用户并为此，应用的捆绑包名称可在许多词类，只要它适合自然用户的请求。

用户将执行的操作的常见任务之一是"verbify"应用程序的名称，即，使应用程序名称，并将其作为在请求中的谓词。 例如， *"MonkeyChat Bobo 这些都很好香蕉。"*

## <a name="the-intents-ui-extension"></a>Intents UI 扩展

Intents UI 扩展提供了机会，将应用程序的 UI 和品牌到 Siri 体验，并使用户感到连接到该应用程序。 借助此扩展插件，该应用程序可以将品牌以及到脚本的可视化和其他信息。

[![](understanding-sirikit-images/intents02.png "Intents UI 扩展的示例输出")](understanding-sirikit-images/intents02.png#lightbox)

Intents UI 扩展将始终返回`UIViewController`和应用程序可以添加任何内容放在视图控制器，例如显示超越了初始响应的其他信息。 Intents UI 还可以使用长时间运行的事件，例如多少就越长滑水感觉的时间共享汽车，到达其位置的状态更新用户。

Intents UI 扩展将始终显示以及其他使用 Siri 内容，例如应用图标和名称在 UI 的顶部或，着眼于基于，可能会在底部显示 （如发送或取消） 按钮。

有少数情况下，应用可以替换 Siri 默认情况下，例如消息显示给用户或映射其中应用程序可以使用一个针对应用程序替换默认的体验的信息。

> [!IMPORTANT]
> 虽然可以添加交互元素，例如`UIButtons`或`UITextFields`意向 UI 扩展到`UIViewController`、 这些严格禁止用作意向 UI 中非交互式的用户将不能与之交互。

它是完全可选的应用程序以提供意图 UI 扩展，因为 Siri 包含一组默认 UI 的每个意向的类型。 此外，Intents UI 接口才提供某些意向 Apple 已被认为是对用户有所帮助。

## <a name="adding-sirikit-vocabulary"></a>添加 SiriKit 词汇

实现 SiriKit 的最后一部分位于应用程序通过提供所需的词汇。 许多应用都有独特的方式的描述向用户和独特的方式，用户将提供到应用的信息的信息。

因此，使用 Siri 需要理解的字词和短语对应用唯一的应用程序的帮助。 一些这些短语将应用程序的一部分，因此每个用户将知道并了解它们。 尚未其他人将是应用的唯一的给定用户。

### <a name="app-specific-vocabulary"></a>特定于应用词汇

应用特定词汇定义的特定字词和短语将已知的所有应用程序的用户，例如车辆类型或健身名称。 由于这些是应用程序的一部分，它们在定义`AppIntentVocabulary.plist`文件作为主应用程序捆绑包的一部分。 此外，还应本地化这些单词和短语。

有几个部分词汇`AppIntentVocabulary.plist`文件：

- **示例应用使用**-这些用户可以进行的应用程序的请求提供一组常见用例。 例如：*"开始测验 MonkeyFit。"*
- **参数**-这些提供一组特定于应用程序的非标准的参数类型。 例如，为 MonkeyFit 应用的健身名称。 这些包括：
    - **短语**-允许定义应用程序的唯一字词应用。 例如： MonkeyFit 应用的"Bananarific"健身类型。 
    - **发音**-发音提示给予 Siri 作为给定短语简单注音拼写。 例如，"ba nana ri 特定"。
    - **示例**-举例说明在应用中使用给定的短语。 例如， *"启动 Bananarific 中 MonkeyFit"*。

有关详细信息，请参阅 Apple[应用词汇文件格式参考](https://developer.apple.com/library/prerelease/content/documentation/Intents/Conceptual/SiriIntegrationGuide/CustomVocabularyKeys.html#//apple_ref/doc/uid/TP40016875-CH10-SW1)。

### <a name="user-specific-vocabulary"></a>用户特定词汇

用户特定词汇打算提供单词或短语是唯一的应用程序的单个用户。 作为一组有序排序中具有列表的开头的最重要条款的用户的最高有效使用优先级的条款，将在运行时从主应用程序 （不应用扩展） 提供这些。

看看上面介绍的 MonkeyChat 应用程序示例。 MonkeyChat 保留的所有用户的联系人，它将发送到通过用户特定词汇的 Siri 的列表。 它还会对用户具有消息的 10 个最新联系人的列表，它具有一组收藏为每个用户的联系人。 对于此示例中，最喜欢的联系人应该是最新的联系人后跟我们用户特定词汇的开头然后用户的联系人信息的其余部分。

用户特定词汇支持以下类型的信息：

- 联系人姓名。
- 健身名称。
- 照片唱片集名称。
- 照片的关键字。

如果应用依赖于 iOS 通讯簿，该应用程序不需要采取任何操作，因为此信息已可供使用 Siri。 应用程序只需提供联系人姓名，如果应用具有其自己的联系人的唯一数据库。

在设计时词汇，仅提供必要的值的用户了解并关注的信息。 避免提供信息，例如电话号码或电子邮件地址。

应用还需要使用 Siri 立即用户特定词汇发生更改时更新。 用户习惯请求信息从 Siri 已添加到其 iOS 设备的时刻。 例如，如果用户在应用程序中添加一个新的联系人，将发送该信息到 Siri 只要用户将其保存。

更重要的是，应用程序_必须_删除信息 Siri 词汇中立即因为用户可能会变得感到不安，如果它们中删除一条信息但数小时或天后，使用 Siri 已仍然识别它。

> [!IMPORTANT]
> 应用程序应从删除所有用户特定词汇的 Siri 如果用户选择重置应用程序，或如果它们注销。

## <a name="sirikit-permissions"></a>SiriKit 权限

最后一段 SiriKit 围绕的权限。 就像使用其他功能 （如照片、 相机或联系人） iOS，用户必须授予应用程序与使用 Siri 的显式权限。

应用程序就能够提供一个字符串，定义哪些信息，它将提供给 Siri 并给出有关为什么用户应授予此访问权限的原因。 

Apple 建议应用程序应使用 Siri 第一次用户打开应用程序，它们在升级到 iOS 10 后向用户请求权限。 这是使用户了解有关使用 Siri 集成，并在进行第一个请求之前，可以预先批准的使用情况。

## <a name="sirikit-and-maps"></a>SiriKit 和映射

SiriKit 是 iOS 不可或缺的一部分，并使用更大的意向框架添加到 iOS 10。 意向 framework 旨在与系统其他部分共享通用和共享的操作和意向。

意向框架超越了只需使用 Siri 集成，并提供其他功能，例如联系人集成的应用程序会变得默认电话服务或消息传送应用程序的特定联系人。 意向还提供与 CallKit 为用户提供最佳 VOIP 体验的深度集成。

在 iOS 10 中的地图应用添加了功能，如持续一段时间共享其中用户可以预订直接在地图 UI 滑水感觉的时间。 SiriKit 提供包含地图的常见扩展点，因此可以 Siri 和 Maps 之间共享骑行共享 （和其他） 意向。 

这意味着，如果应用已采用 SiriKit 扩展，它还将获得地图集成免费。 

## <a name="designing-a-great-siri-experience"></a>设计出色的 Siri 体验

将应用集成到 Siri 时设计出色的用户体验是不同于设计出色的应用程序用户界面。 与不同的是正常的情况下，在用户交互与该应用程序是直接在屏幕上，存在使用 Siri 时很多时候时没有可视化界面是可见的。 例如，当用户已开始与对话 *"您好 Siri"*。

### <a name="how-siri-helps-the-developer"></a>使用 Siri 如何帮助开发人员

在设计时使用 Siri 交互的应用，将生成应用*交谈界面*，这意味着上下文派生自 Siri 具有与代表应用程序的用户的会话。

如果没有可视参考，用户必须跟踪的其头中显示的信息。 因此，使用 Siri 显示裸机最小所需的信息来完成任务的用户希望完成。

交谈界面的形状的问题和响应来自用户和 Siri 在对话期间。 因此务必考虑如何使用 Siri 会询问一些问题和时设计此界面的响应。

以下示例创建一条消息，Siri 使用问题，可能会响应用户的 *"准备将其发送？"*. 用户可以如以多种不同方式做出响应 *"发送"*， *"取消"* 或甚至一些毫不相关对此问题。 如何会话过程的运作，无论使用 Siri 将处理的应用程序中，并仅将其发送的相关信息变得可用。

有多种不同的方式，用户可能会启动与 Siri 的会话：

- 通过选择设备，按主页按钮。 在此情况下使用 Siri 会显示更多 visual 接口和更少口头响应。
- 指明 *"您好 Siri"* 和启动手免费会话。 在此情况下使用 Siri 将是不太 visual 和更文字。
- 使用可访问性功能，例如蓝牙启用听力辅助工具用户界面将针对具有特殊需求的用户。
- 使用汽车播放用户需要保留他们的注意力专注于提高通过保持在最低限度的干扰。

### <a name="how-the-developer-helps-siri"></a>开发人员如何帮助使用 Siri

当使用 Siri 集成应用程序，开发人员需要测试通常这种集成，并确保它们通过请求相同的信息或任务中有多少种尽可能使许多不同的请求。

由于没有两个人们认为等内容，因此很重要，开发人员获取任意多个不同的 beta 版本测试人员，以帮助微调 Siri 集成。 用户可能会要求提供信息或发出请求的方式在开发人员永远不会但是的和此优化可帮助确保最广泛的用户组具有自己的应用程序中使用 Siri 更完美的体验。

在不同的情况下和环境中测试。 启动会话的 Siri 中的所有方法可以确保这些会话保持流畅和自然。 测试在其中用户将很可能使用应用程序中，如在拥挤健身房中的位置。

请确保该应用程序提供的所有信息 Siri 需要正确表示用户的请求和结果。 当在手中可用的情况下使用 Siri 时，也是如此。

### <a name="siri-design-guidelines"></a>使用 Siri 设计指南

务必记住 Siri 代表应用程序具有与用户的会话。 开发人员希望为不确定此会话保持一样流畅和自然尽可能。

就像与任何重要的会话，开发人员需要确保满足以下：

- 会话将准备应用程序。
- 应用程序侦听完全哪些用户正在尝试完成。
- 应用会在适当的时间要求相应的问题。
- 应用响应请求查找用户的信息。

#### <a name="preparing-for-the-conversation"></a>为会话准备

第一个需要记住的一点是，不会应用的用户完全一样，开发人员。 也可能来自不同背景、 从讲不同语言或使用应用程序时有特殊需求。

此外，因为开发人员设计和构建应用程序，它们深入，有足够了解的应用程序和其内部工作情况和典型的用户不会的函数。 因此，开发人员可能会不同于普通用户要求 Siri 请求。

这就是原因，当务之急在许多不同的人，尽可能与通过 Siri 应用进行交互。 用户可能会使开发人员具有也从未想过的或在开发人员未考虑的方面的 Siri 通过应用的请求。

#### <a name="ensure-the-app-is-a-good-listener"></a>确保应用程序是一个很好的侦听器

开发人员需要确保应用程序是一个很好的侦听器，并获取满足用户的期望会话的详细信息。 但是，还有可能，它们可能未提供所有应用程序需要以实现请求的任务的信息。

有几种方法，该应用程序无法处理这种情况：

- **请为缺少的值选择很好的默认**-例如滑水感觉的时间共享应用程序可能默认为当前用户的位置，如果他们没有指定他们想要从提取。
- **凭经验猜测**-使用应用程序收集用户的特定信息，该应用程序可能能够品牌和凭经验猜测上缺少的信息，如填写缺少的移动电话号码从用户的联系信息。 但是，应格外小心，以避免错误意外情况，例如选取最高的选项，等等。
- **提示输入更多信息**-应用程序可以提示用户输入缺失值时使用 Siri。 但是，此处的关键简单和到点保持会话。 用户将迅速成为感到沮丧，如果他们需要回答以下几个问题，可以实现其请求。
- **误报适当地处理**-用户可能会提供一个应用程序不是预期或它不能处理给定的上下文中的值。 请确保该应用程序与这种情况下使其清晰、 易才能更正的方式中的用户。

当与单个值的问题提供应用程序时，处理这种情况的首选的方法是具有 Siri 要求用户确认。 例如， *"你的意思 Bobo 很好？"*，其中他们可以使用一个简单的是或否答案回复。

如果有多个可能的选项可能是正确的单个值的情况下，消除二义性是首选的处理方法。 在此情况下使用 Siri 可以提示具有最多十个可能的选项可供选择的用户。 例如：

```csharp
Who do you want to send the message to?

* Bobo the Great!
* Bobo Jr.
* Little Bobo
```

如果仍在问题，必须使用 Siri 提示用户提供的给定值的一个全新、 更具针对性的答案。

#### <a name="request-final-confirmation"></a>请求最终确认

该应用程序实际执行的任务，以满足用户的请求之前，使用 Siri 将检查与应用扩展，以确保一切已准备就绪。 例如，该用户是否具有足够的资金用他们的帐户进行请求的付款？

此外，应用程序需要确保，它会向所有可能的信息到 Siri 使它能够向用户提供并确认要执行的任务满足其期望。

一旦用户确认请求和应用程序都没有执行它，以再次确保它具有提供的所有结果返回到 Siri 以便它可以将其关联到用户的应用程序需求。

#### <a name="responding-to-the-request"></a>对请求做出响应

使用 Siri 有几个内置的用户界面的每个域和它所知道的操作。 但是，在适当的情况应用程序可以提供一个自定义意向 UI 扩展，用于通过提供应用的品牌和 UI 或不是在请求中存在的详细信息，丰富用户体验。

话虽如此，但为 Siri 设计自定义接口时，应使用避免失误。 通常情况下，用户希望获取尽可能快地完成特定任务，而不想重载与不必要的信息。

此外应格外小心以确保自定义 UI 的外观和正确响应中的所有不同的 iOS 设备和用户可能具有或正在使用设备的方向。

在适当时使用 SiriKit API 隐藏默认 Siri UI 中已存在任何冗余信息。 还确保该应用程序仍提供信息 siri 以便它可以显示它口头在手中可用的情况下。

可能情况下使用 Siri 将会启动应用以满足用户的请求，如显示用户已请求的照片。 在这些情况下，不要感到惊讶用户。 显示所期望的信息，而无需进一步交互或中间步骤。 永远不会显示信息或执行用户不希望的任务。

### <a name="polishing-the-design"></a>改进设计

有 Apple 建议来改进的交谈界面设计的几个步骤。 首先，是通过提供清晰、 简洁词汇和使用用例示例 siri。

用户发现应用程序的方法之一是通过启动会话使用 Siri 和要求， *"可以您做什么？"* 使用 Siri 将显示几个不同的事物，它可以执行操作，包括开发人员的应用程序和示例 hero 用例，它提供了通过其`plist`文件。

如何编写良好示例用例：

- 请确保的示例包括应用名称。
- 保持示例简短和点到。
- 为每个应用程序支持的方式提供多个示例。
- 确定优先级意向，其中基于应用的最常见用例的示例。
- 请确保该应用程序提供了本地化的示例。
- 确保给定的工作原理，按预期方式应用中的每个示例。
- 避免在示例中，因此，不包括文本等寻址 Siri *"您好 Siri..."*
- 避免任何不必要 pleasantries *"请"* 或 *"谢谢"*。

需要适当的时间进行探索和试验上应用程序可以将如何调整 Siri 具有与代表其用户的会话。 请确保作为与的交互通信与典型用户在整个过程，并可能随时间变化的应用程序的预期。

始终记住测试不同的情况下应用和所有不同的方法调用与 Siri 的会话。 测试在现实世界位置中用户的可能正在使用的应用，使 office 和支持人员。

致力于与进行对话使用 Siri （代表应用程序） 是流畅、 自然和"感觉还是恰好合适"。 

## <a name="summary"></a>总结

本文只讨论了需要使用 SiriKit 并显示它可以与 xamarin ios 应用提供的 iOS 设备上使用 Siri 和 Maps 应用的用户可以访问的服务进行交互的重要概念。




## <a name="related-links"></a>相关链接

- [ElizaChat 示例](https://developer.xamarin.com/samples/monotouch/ios10/ElizaChat/)
- [SiriKit 编程指南](https://developer.apple.com/library/prerelease/content/documentation/Intents/Conceptual/SiriIntegrationGuide/index.html)
- [意向框架引用](https://developer.apple.com/reference/intents)
- [Intents UI 框架引用](https://developer.apple.com/reference/intentsui)
