---
title: 使用 CocoaPods 的真实示例
description: 本文档演示如何使用目标 Sharpie 自动生成C#绑定中 CocoaPod 的定义。
ms.prod: xamarin
ms.assetid: 233B781D-5841-4250-9F63-0585231D2112
author: asb3993
ms.author: amburns
ms.date: 03/28/2018
ms.openlocfilehash: 266f2bca1f4a96242b17080e60c9f43cb956a5fd
ms.sourcegitcommit: bf18425f97b48661ab6b775195eac76b356eeba0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2019
ms.locfileid: "64977871"
---
# <a name="real-world-example-using-cocoapods"></a>使用 CocoaPods 的真实示例

> [!NOTE]
> 此示例使用[AFNetworking CocoaPod](https://cocoapods.org/pods/AFNetworking)。

3.0 版开始中的新增功能目标 Sharpie 支持绑定 CocoaPods，，甚至可以包括一个命令 (`sharpie pod`) 进行下载、 配置和构建 CocoaPods 非常简单。 您应该[熟悉 CocoaPods](https://cocoapods.org)一般情况下再使用此功能。

## <a name="creating-a-binding-for-a-cocoapod"></a>为 CocoaPod 创建绑定

`sharpie pod`命令包含一个全局选项和两个子命令：

```bash
$ sharpie pod -help
usage: sharpie pod [OPTIONS] COMMAND [COMMAND_OPTIONS]

Pod Options:
  -d, -dir DIR     Use DIR as the CocoaPods binding directory,
                   defaulting to the current directory

Available Commands:
  init         Initialize a new Xamarin C# CocoaPods binding project
  bind         Bind an existing Xamarin C# CocoaPods project
```

`init`子命令还具有一些有用的帮助：

```bash
$ sharpie pod init -help
usage: sharpie pod init [INIT_OPTIONS] TARGET_SDK POD_SPEC_NAMES

Init Options:
  -f, -force       Initialize a new Podfile and run actions against
                   it even if one already exists
```

多个 CocoaPod 名称和 subspec 名称可以提供给`init`。

```bash
$ sharpie pod init ios AFNetworking
** Setting up CocoaPods master repo ...
   (this may take a while the first time)
** Searching for requested CocoaPods ...
** Working directory:
**   - Writing Podfile ...
**   - Installing CocoaPods ...
**     (running `pod install --no-integrate --no-repo-update`)
Analyzing dependencies
Downloading dependencies
Installing AFNetworking (2.6.0)
Generating Pods project
Sending stats
** 🍻 Success! You can now use other `sharpie podn`  commands.
```

一旦您 CocoaPod 已设置了，现在可以创建绑定：

```bash
$ sharpie pod bind
```

这将导致 CocoaPod Xcode 项目正在生成，然后计算以及由目标 Sharpie 进行分析。 大量的控制台输出将会生成，但应导致末尾处的绑定定义：

```bash
(... lots of build output ...)

Parsing 19 header files...

Binding...
  [write] ApiDefinitions.cs
  [write] StructsAndEnums.cs

Done.
```

## <a name="next-steps"></a>后续步骤

生成后**ApiDefinitions.cs**并**StructsAndEnums.cs**文件，看一下生成的程序集，若要在应用中使用的以下文档：

- [绑定 OBJECTIVE-C 的概述](~/cross-platform/macios/binding/overview.md)
- [绑定 OBJECTIVE-C 库](~/cross-platform/macios/binding/objective-c-libraries.md)
- [演练：绑定 iOS OBJECTIVE-C 库](~/ios/platform/binding-objective-c/walkthrough.md)
