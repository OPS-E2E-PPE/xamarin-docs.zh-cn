---
title: 第 6 部分 - 测试和应用商店审批
description: 本文档介绍如何测试跨平台应用程序上的设备、 管理测试用例、 自动测试、 运行单元测试和解决应用程序提交过程。
ms.prod: xamarin
ms.assetid: 46E0578A-7EB9-C105-ABB0-A043E501F36B
author: asb3993
ms.author: amburns
ms.date: 03/23/2017
ms.openlocfilehash: 0faf7c9e4ff7c96cdfd25ab6d6658726ef247b32
ms.sourcegitcommit: 4b402d1c508fa84e4fc3171a6e43b811323948fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61275402"
---
# <a name="part-6---testing-and-app-store-approvals"></a>第 6 部分 - 测试和应用商店审批

## <a name="testing"></a>正在测试

许多应用程序 （甚至上的 Android 应用，某些存储） 将需要发布; 经过审批过程因此测试是很关键，以确保您的应用程序达到市场 （更不用说你的客户成功）。 测试可采取多种形式，从开发人员级别的单元测试与管理 beta 测试跨各种硬件。

### <a name="test-on-all-platforms"></a>在所有平台上进行测试

有一些细微的差别之间.NET 支持在 Windows 手机、 平板电脑和桌面设备，以及防止动态生成动态代码的 iOS 上的限制。 可以将计划测试上多个平台的代码，因为你开发，或计划进行重构的时间和更新你的应用程序项目末尾处的模型部分。

它始终是使用模拟器/模拟器来测试多个版本的操作系统以及不同的设备功能/配置的好办法。

此外应尽可能的任意多个不同的物理硬件设备上进行测试。

#### <a name="devices-in-cloud"></a>在云设备

移动电话和平板电脑生态系统总是在增长，因此无法在不断增加的可用设备数上进行测试。 若要解决此问题多个服务提供的功能，以便应用程序可以安装和测试而无需直接投入大量硬件远程控制许多不同设备。

[App Center 测试](https://docs.microsoft.com/appcenter/test-cloud/preparing-for-upload/uitest)提供简单的方法来测试 iOS 和 Android 应用程序上几百个不同的设备。

### <a name="test-management"></a>测试管理

当测试你的组织或与外部用户管理测试计划中的应用程序时，有两个难题：

- **分发**– 管理 （尤其是对于 iOS 设备） 预配过程并获取更新的版本的软件测试人员。
- **反馈**– 收集有关应用程序使用情况信息和详细的信息可能会发生任何错误。


有多种服务可以帮助解决这些问题，通过提供基础结构构建到你的应用程序来收集和报告的使用情况和错误，并还同时精简预配过程来帮助注册并管理测试人员和他们的设备.

[Visual Studio App Center](/appcenter/)提供了这些问题，提供测试版本分发、 崩溃报告和复杂的应用程序使用情况信息的解决方案。

### <a name="test-automation"></a>测试自动化

Xamarin [UITest](https://docs.microsoft.com/appcenter/test-cloud/preparing-for-upload/uitest)可用于创建测试脚本，以便可以在本地运行或上传到的自动化的用户界面[App Center 测试](https://docs.microsoft.com/appcenter/test-cloud/)。

## <a name="unit-testing"></a>单元测试

### <a name="touchunit"></a>Touch.Unit

Xamarin.iOS 包括一个称为 Touch.Unit 遵循 JUnit/NUnit 样式编写测试的单元测试框架。

请参阅我们[单元测试使用 Xamarin.iOS](~/ios/deploy-test/touch.unit.md)编写测试，并运行 Touch.Unit 的详细信息的文档。

### <a name="andrunit"></a>Andr.Unit

没有适用于 Android 调用 Andr.Unit Touch.Unit 开放源代码等效项。 你可以下载它从[github](https://github.com/spouliot/Andr.Unit)上了解该工具[@spouliot的博客](http://spouliot.wordpress.com/2011/10/30/andr-unit-joins-the-family/)。

## <a name="app-store-approvals"></a>应用商店审批

Apple 和 Microsoft 操作在其平台上的唯一存储： 应用商店和 Marketplace 分别。 同时使用锁定其设备并实现严格的应用程序检查过程来控制应用程序可供下载的质量。 Android 的开放性质意味着数范围从 Google Play，其广泛可用，但具有无审核过程，Amazon 的应用商店的 Android 和特定于硬件的恢复所需的更多限制分发 Samsung 应用到的存储选项并实现了审批过程。

等待要审阅的应用可以是很大的压力-商业压力通常意味着使用"目标"的启动日期之前的错误很少边距的应用程序提交以供审核。 进程本身可能需要最多两周，不一定是透明： 有是应用程序的进度有限的反馈，直到最后被拒绝或获得批准。 特别是它发生一次以上，并通过在原始发布日期之间的周以及最后批准应用时拒绝可能意味着缺少了市场营销机会，窗口。

### <a name="be-prepared"></a>做好准备

建议的第一条： 早早提前规划应用程序的启动和补偿可能拒绝和重新提交。 每个存储要求你将应用提交之前创建一个帐户-尽早执行此操作。
Google Play 注册只需要几分钟，如果您的应用程序是免费，而过程获取更多涉及，如果您销售产品，并需要提供银行和税务信息。 Apple 和 Microsoft 的进程是同时比 Google 的复杂得多，可能需要一周或更多以获取您批准的帐户因此，应考虑这一次启动计划。

在你的帐户获得批准，现在即可提交应用程序。 提交应用程序的实际过程介绍了以下文档：

- [发布到 Apple 的 iOS 应用商店](~/ios/deploy-test/app-distribution/app-store-distribution/publishing-to-the-app-store.md)
- [Google play 准备应用](~/android/deploy-test/publishing/publishing-to-google-play/index.md)
- 请访问 Windows 开发人员应[Windows 开发人员中心](https://developer.microsoft.com/windows/windows-apps)若要了解提交其应用程序。

本部分的其余部分讨论的操作应考虑到以确保您的应用程序批准而无需任何和谐的因素。

### <a name="quality"></a>质量

这听起来很明显，但因为它们不符合特定级别的质量通常被拒绝的应用程序： 毕竟，这是为什么组织有序的存储都具有审批流程第一个位置中的原因 ！

崩溃是拒绝的常见原因。 如果它是很容易会导致应用出现故障，它保证被拒绝。 大多数开发人员不提交其应用的假定条件下，它们将崩溃，但它们通常执行的操作。 进行全面测试您的应用程序之前将其提交，将重点放不局限于以确保一切正常，但还你处理常用移动错误方案，如网络问题和资源约束，例如内存或存储空间。 使用模拟器和物理设备测试-无论程度代码运行在模拟器中，唯一的设备可演示应用程序的实际性能。 使用任意多个不同的设备可以查找，并登记的 beta 版测试人员团队，如果您可以-第三方服务可以帮助管理 beta 分发和反馈。

所有的移动操作系统将终止不会足够快速地启动应用程序。 允许的时间长度可变的但一般情况下应用的目标应该响应几秒钟后，使用后台任务执行任何作业都将耗时更长。 应用程序需要很长时间加载或不足够的响应能力中经常使用的是将被拒绝。 发生在后台，或应用程序将会显示已崩溃和再一次被拒绝时，始终提供用户反馈。

### <a name="check-your-edge-cases"></a>检查边缘情况

开发人员的常见陷阱故障到地址边缘的情况下，特别是那些需要重新配置其模拟器或设备来测试正确。 它可以很容易忘记，并非每个客户会转到"允许"您的应用程序访问它们的位置，因为开发人员一次接受该请求后，它们将永远不会再次提示输入。 权限和网络使用情况是专门专注于在批准过程中，这意味着在这些领域小监督可能会导致拒绝。

以下列表是很好的起点，用于检查可能错过的边缘情况：

- **客户可能会 deny 对服务的访问**– 尤其是在 iOS 中，对数据的访问，例如，如果用户授予对你的应用程序的权限，则仅提供地理位置信息。 应用程序测试人员应该经常重新安装它的初始状态中的应用程序和不允许任何权限请求，以确保应用程序运行正常。 关闭以验证正确的行为，如客户改变想法和切换上的权限。
- **到处都有客户**– 不要认为应用程序将仅使用城市或国家/地区开发 ！ 适用于 GPS 坐标、 日期和时间值和货币的代码可以所有受客户的位置和区域设置。 所有平台都可以提供一个模拟器，允许您指定不同的位置和区域设置-都使用它来测试在其他两个半球，并且以不同方式设置日期和货币的格式的区域性的位置。 纬度和经度值可以是正数或负数、 小数点分隔符可能是一个句点或逗号，和可以设置日期格式大量的方式-解决这个问题 ！
- **网络连接速度缓慢**– 应用程序开发人员通常在理想的快速、 始终使用网络连接，显然不是这种情况在现实世界中工作。 测试与慢速网络连接 （例如 3g 连接不佳） 以及没有网络访问权限是至关重要的确保不提供错误的应用程序。 审批过程将使用飞行模式中的设备将始终包含的测试，因此请确保，你已自行测试的。
- **硬件而异**– 请记住在你打算支持的最早、 最慢的硬件上进行测试。 有可能会影响您的应用程序的两个方面： 性能，这可能是较旧的设备和支持的硬件功能，例如照相机、 麦克风、 GPS、 陀螺仪或其他可选组件不可用。 应会降低应用程序正常 （和不崩溃） 时不可用的组件。

### <a name="guidelines-are-more-than-just-a-guide"></a>指导原则是不止是指南

Apple 是因严格遵守其人机接口指南 》 的因为其平台的关键优势之一是一致性 （和可用性的感知的增加）。 Microsoft 已与实现美俏风格用户界面的 Windows 应用程序采取类似的方法。 这两个平台的审批过程将与你的应用进行计算以用于其遵守相关的设计理念。

这不是说，用户界面创新并不受支持或建议，但有某些"只是不应执行的操作"，或您的应用程序将被拒绝。

在 iOS 上，这包括误用内置图标或使用其他成功建立的隐喻以非一致的方式;有关创建新的内容之外的任何内容，例如使用撰写图标。

Windows 开发人员应同样谨慎;一个常见错误无法正确支持硬件返回根据 Microsoft 的指导原则的按钮。

鼓励设计人员可以阅读并遵循每个平台的设计指南。

### <a name="implementing-platform-specific-features"></a>实现特定于平台的功能

尤其是在 iOS 上实现特定于平台的服务时，情况就有点更严格。 若要避免通过 Apple 的自动拒绝，有与以下 iOS 功能遵循一些规则：

- **应用内购买**– 应用程序必须实现数字产品包括在游戏货币、 应用程序功能、 杂志订阅和更多的外部的付款机制。 iOS 应用程序必须使用 Apple 的 iTunes 基于服务，用于此类功能。 没有一漏洞的应用程序等 Kindle 读取器和某些基于订阅的应用，可以购买其他位置的内容会附加到你可以通过应用访问的"帐户"，但是在这种情况下不包含应用程序必须链接或引用应用程序外购买过程 （或者，再次重申，将被拒绝）。
- **iCloud 备份**– 使用 iCloud 的问世，Apple 的审阅者具备更严格有关应用如何使用存储 （以确保客户的远程备份体验愉快）。 应用程序，可能会被拒绝的废物可备份的存储空间，因此使用缓存文件夹正确并按照 Apple 的其他存储相关的指导原则。
- **Newsstand** – 报纸和杂志应用是非常适合用于 Apple Newsstand，但应用程序必须实现至少一种自动续订订阅和支持后台下载将被批准。
- **映射**– 情况越来越常见，将覆盖和其他功能添加到移动映射，但是请注意不会影响映射额度信息 （如 iOS5 中的 Google 徽标） 因为执行此操作会导致拒绝。

### <a name="manage-your-metadata"></a>管理你的元数据

除了可能会导致被拒绝的应用程序的明显技术问题，还有一些更加微妙的方面，你可能会导致拒绝，尤其是在方面的元数据 （说明、 关键字和市场营销的映像），您的提交内容提交用于 App Store 或 Marketplace 中显示应用程序。

- **图像**– 遵循平台的应用程序图标的准则和存储图片。 不要使用商标字的映像，我们已了解应用程序获取拒绝，因为其图标特色 iPhone 的绘图 ！
- **商标**– 请避免使用你自己的以外的任何商标。 应用程序已被拒绝的一提的是在应用程序说明或甚至在 Apple 的 App Store 上的关键字的商标。
- **说明**– 不使用单词 beta 或以任何方式指示应用程序不是大有作为。 未涉及其他移动平台 （即使您的应用程序是跨平台）。 最重要的是，请确保完全什么您说它执行的应用执行。 如果在说明中列出一系列功能，则它最好做好明显如何使用每个这些功能，否则将显示"未实现应用程序的说明中提到的功能"拒绝。

将放到开发和测试太多工作拆分为应用程序的元数据。 应用程序执行操作的元数据中的次要侵权行为被拒绝，因此很值得花时间正确。

### <a name="app-stores-not-for-everyone"></a>应用商店：不为每个人

每个平台上存储的主要重点是使用者分发-能够尽可能达到尽可能多的客户。 但是并非所有应用程序为目标的使用者在没有快速增长的需要有限的分发给员工、 供应商或客户的内部和外部网络类似于应用程序基。 这些应用不是"for sale"，并不需要审批，因为开发人员控件分发给一组已关闭的用户。
对部署此类型的支持因平台而异。

Android 提供了最大的灵活性在这方面: （只要该设备的配置允许该操作），可以直接从 URL 或电子邮件附件安装应用程序。 这意味着它轻松地创建和分发内部的企业应用程序或应用程序发布到特定客户或供应商。

Apple 在 iOS 开发人员企业计划，这会绕过应用商店审批流程，可让公司将分发给其员工的内部应用程序中注册的开发人员提供了一个内部部署选项。
遗憾的是此许可证不能解决需要 extranet 类似的应用分发到客户或供应商的其他关闭的组。 [Enterprise （和 Ad Hoc） 部署](~/ios/deploy-test/app-distribution/ipa-support.md)

### <a name="app-store-summary"></a>应用商店摘要

审核过程会非常艰巨，但像开发生命周期的其余部分可帮助确保成功使用一些规划和注意细节。 这完全取决于几个简单步骤： 阅读和理解必须遵循，遵循的规则，如果要实现特定于平台的功能，全面测试 （然后测试的更多） 和最后请确保你的应用程序元数据的用户界面指南在提交之前正确无误。

建议对开发人员在 Google Play 上发布一个最后一个单词： 缺少的审批过程可能看起来像它使您的工作更轻松的但你的客户将会评审团队的更多要求。 因为尽管您的应用程序可能被拒绝，否则它将为你执行拒绝的客户，请遵循以下准则。
