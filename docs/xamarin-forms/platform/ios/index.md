---
title: 在 Xamarin.Forms 中的 iOS 平台功能
description: 将特定于 iOS 的功能添加到 Xamarin.Forms 应用程序。
ms.prod: xamarin
ms.assetid: 634AB62E-68C8-454C-838B-F1CC4E4E21BC
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 02/22/2019
ms.openlocfilehash: 7aa9d298c2219dff60ca8ca1f917c72194ad21ca
ms.sourcegitcommit: 0fd04ea3af7d6a6d6086525306523a5296eec0df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512684"
---
# <a name="ios-platform-features-in-xamarinforms"></a>在 Xamarin.Forms 中的 iOS 平台功能

开发适用于 iOS 的 Xamarin.Forms 应用程序需要 Visual Studio。 [要求页](~/get-started/requirements.md)包含有关系统必备组件的详细信息。

## <a name="platform-specifics"></a>平台特定信息

平台特定信息，可使用的功能仅适用于特定的平台，而无需实现自定义呈现器或效果。

Xamarin.Forms 视图、 页面和 iOS 上的布局提供了以下特定于平台的功能：

- 模糊处理的任何支持[ `VisualElement` ](xref:Xamarin.Forms.VisualElement)。 有关详细信息，请参阅[在 iOS 上 VisualElement 模糊](visualelement-blur.md)。
- 禁用上受支持的旧颜色模式[ `VisualElement` ](xref:Xamarin.Forms.VisualElement)。 有关详细信息，请参阅[VisualElement 旧式颜色模式在 iOS 上](legacy-color-mode.md)。
- 在启用投影[ `VisualElement` ](xref:Xamarin.Forms.VisualElement)。 有关详细信息，请参阅[VisualElement 删除阴影的 iOS](visualelement-drop-shadow.md)。

以下特定于平台的功能用于在 iOS 上的 Xamarin.Forms 视图：

- 设置[ `Cell` ](xref:Xamarin.Forms.Cell)背景色。 有关详细信息，请参阅[在 iOS 上的单元格背景色](cell-background-color.md)。
- 确保输入的文本适合[ `Entry` ](xref:Xamarin.Forms.Entry)通过调整字体大小。 有关详细信息，请参阅[条目在 iOS 上的字体大小](entry-font-size.md)。
- 在中设置的游标颜色[ `Entry` ](xref:Xamarin.Forms.Entry)。 有关详细信息，请参阅[在 iOS 上的条目游标颜色](entry-cursor-color.md)。
- 控制是否[ `ListView` ](xref:Xamarin.Forms.ListView)标头单元格浮动在滚动过程。 有关详细信息，请参阅[在 iOS 上的 ListView 组标头样式](listview-group-header-style.md)。
- 控制是否禁用行动画时[ `ListView` ](xref:Xamarin.Forms.ListView)正在更新项集合。 有关详细信息，请参阅[在 iOS 上的 ListView 行动画](listview-row-animations.md)。
- 设置分隔符样式[ `ListView` ](xref:Xamarin.Forms.ListView)。 有关详细信息，请参阅[在 iOS 上的 ListView 分隔符样式](listview-separator-style.md)。
- 控制当项选择发生在[ `Picker` ](xref:Xamarin.Forms.Picker)。 有关详细信息，请参阅[选取器在 iOS 上的项选择](picker-selection.md)。
- 启用[ `Slider.Value` ](xref:Xamarin.Forms.Slider.Value)属性可以通过点击对一个位置上设置[ `Slider` ](xref:Xamarin.Forms.Slider)栏中，而不是按无需将`Slider`thumb。 有关详细信息，请参阅[在 iOS 上的滑块 Thumb 点击](slider-thumb.md)。

在 iOS 上的 Xamarin.Forms 页面提供以下特定于平台的功能：

- 在隐藏导航栏分隔符[ `NavigationPage` ](xref:Xamarin.Forms.NavigationPage)。 有关详细信息，请参阅[NavigationPage Bar Separator 在 iOS 上](navigation-bar-separator.md)。
- 控制是否半透明的导航栏。 有关详细信息，请参阅[在 iOS 上的导航栏半透明度](navigation-bar-translucent.md)。
- 控制是否状态栏文本的颜色上[ `NavigationPage` ](xref:Xamarin.Forms.NavigationPage)调整以匹配导航栏的亮度。 有关详细信息，请参阅[NavigationPage 栏文本颜色模式在 iOS 上](status-bar-text-color.md)。
- 控制是否将页标题显示为页导航栏中的大型标题。 有关详细信息，请参阅[在 iOS 上的大型页标题](page-large-title.md)。
- 设置家庭指示器的可见性[ `Page` ](xref:Xamarin.Forms.Page)。 有关详细信息，请参阅[主页在 iOS 上的指示符可视性](page-home-indicator.md)。
- 设置状态条可见性[ `Page` ](xref:Xamarin.Forms.Page)。 有关详细信息，请参阅[在 iOS 上的页状态条可见性](page-status-bar-visibility.md)。
- 确保该页面内容位于上是安全的所有 iOS 设备的屏幕区域。 有关详细信息，请参阅[在 iOS 上的安全区域布局指南](page-safe-area-layout.md)。
- 在 iPad 上设置模式页面演示文稿的样式。 有关详细信息，请参阅[iPad 模式页面演示文稿样式](ipad-page-presentation-style.md)。

以下特定于平台的功能用于在 iOS 上的 Xamarin.Forms 布局：

- 控制是否[ `ScrollView` ](xref:Xamarin.Forms.ScrollView)处理触摸手势或将其传递给其内容。 有关详细信息，请参阅[ScrollView 内容涉及 iOS](scrollview-content-touches.md)。

以下特定于平台的功能提供适用于 Xamarin.Forms [ `Application` ](xref:Xamarin.Forms.Application)在 iOS 上的类：

- 正在禁用针对命名的字体大小进行扩展的可访问性。 有关详细信息，请参阅[辅助功能针对在 iOS 上名为字体大小进行扩展](named-font-size-scaling.md)。
- 启用控件的布局和呈现要在主线程上执行更新。 有关详细信息，请参阅[在 iOS 上的主线程控制更新](main-thread-updates-ui.md)。
- 启用[ `PanGestureRecognizer` ](xref:Xamarin.Forms.PanGestureRecognizer)中滚动视图来捕获和共享平移手势与滚动视图。 有关详细信息，请参阅[在 iOS 上的同时进行平移手势识别](application-pan-gesture.md)。

## <a name="ios-specific-formatting"></a>特定于 iOS 的格式设置

Xamarin.Forms 支持跨平台用户界面样式和颜色设置的但有其他选项来设置你的 iOS 使用平台 Api 的 iOS 项目中的主题。

[阅读更多](formatting.md)有关格式设置使用特定于 iOS 的 Api，如用户界面**Info.plist**配置和`UIAppearance`API。

![](images/status-white-sml.png "iOS 主题设置")

## <a name="other-ios-features"></a>其他 iOS 功能

使用[自定义呈现器](~/xamarin-forms/app-fundamentals/custom-renderer/index.md)，则[DependencyService](~/xamarin-forms/app-fundamentals/dependency-service/index.md)，并[MessagingCenter](~/xamarin-forms/app-fundamentals/messaging-center.md)，可以纳入各种各样的本机功能集成到适用于 iOS 的 Xamarin.Forms 应用程序。
