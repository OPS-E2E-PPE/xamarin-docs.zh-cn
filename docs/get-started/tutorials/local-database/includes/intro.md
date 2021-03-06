---
ms.openlocfilehash: 004d7df72103ef332f802bd0019d2a99c6cc11a2
ms.sourcegitcommit: a153623a69b5cb125f672df8007838afa32e9edf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2019
ms.locfileid: "67277120"
---
开始演练本教程的前提条件为已成功完成以下教程：

- [生成第一个 Xamarin.Forms 应用](~/get-started/first-app/index.md)快速入门。
- [StackLayout](~/get-started/tutorials/stacklayout/index.yml)教程。
- [按钮](~/get-started/tutorials/button/index.yml)教程。
- [输入](~/get-started/tutorials/entry/index.yml)教程。
- [ListView](~/get-started/tutorials/listview/index.yml) 教程。

在本教程中，你将了解：

> [!div class="checklist"]
> - 使用 NuGet 包管理器将 SQLite.NET 添加到 Xamarin.Forms 项目。
> - 创建数据访问类。
> - 使用数据访问类。

你将使用 Visual Studio 2019 或 Visual Studio for Mac 创建一个简单的应用程序，演示如何将数据存储在本地 SQLite.NET 数据库中。 以下屏幕截图显示了最终的应用程序：

[![iOS 和 Android 上的本地 SQLite.NET 数据库数据暂留的屏幕截图](../images/consume-data-access-classes-reduced.png "本地数据库数据暂留")](../images/consume-data-access-classes-large.png#lightbox "Local database data persistence")
