---
title: 在 iOS 上 VisualElement 删除阴影
description: 平台特定信息，可使用的功能仅适用于特定的平台，而无需实现自定义呈现器或效果。 本文介绍如何使用平台特定于 iOS 的使上 VisualElement 投影。
ms.prod: xamarin
ms.assetid: 2147FD66-058E-4BE5-840A-369842B26EC4
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 10/24/2018
ms.openlocfilehash: 9c576be30eb4b456e2eabcb5a041c57e58bdc747
ms.sourcegitcommit: b23a107b0fe3d2f814ae35b52a5855b6ce2a3513
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2019
ms.locfileid: "65925642"
---
# <a name="visualelement-drop-shadows-on-ios"></a>在 iOS 上 VisualElement 删除阴影

[![下载示例](~/media/shared/download.png)下载示例](https://developer.xamarin.com/samples/xamarin-forms/UserInterface/PlatformSpecifics/)

此平台特定于 iOS 的用于上启用投影[ `VisualElement` ](xref:Xamarin.Forms.VisualElement)。 设置使用在 XAML [ `VisualElement.IsShadowEnabled` ](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.IsShadowEnabledProperty)附加到属性`true`，以及许多其他可选的附加控制投影的属性：

```xaml
<ContentPage ...
             xmlns:ios="clr-namespace:Xamarin.Forms.PlatformConfiguration.iOSSpecific;assembly=Xamarin.Forms.Core">
    <StackLayout Margin="20">
        <BoxView ...
                 ios:VisualElement.IsShadowEnabled="true"
                 ios:VisualElement.ShadowColor="Purple"
                 ios:VisualElement.ShadowOpacity="0.7"
                 ios:VisualElement.ShadowRadius="12">
            <ios:VisualElement.ShadowOffset>
                <Size>
                    <x:Arguments>
                        <x:Double>10</x:Double>
                        <x:Double>10</x:Double>
                    </x:Arguments>
                </Size>
            </ios:VisualElement.ShadowOffset>
         </BoxView>
        ...
    </StackLayout>
</ContentPage>
```

或者，可以使用它从 C# 使用 fluent API:

```csharp
using Xamarin.Forms.PlatformConfiguration;
using Xamarin.Forms.PlatformConfiguration.iOSSpecific;
...

var boxView = new BoxView { Color = Color.Aqua, WidthRequest = 100, HeightRequest = 100 };
boxView.On<iOS>()
       .SetIsShadowEnabled(true)
       .SetShadowColor(Color.Purple)
       .SetShadowOffset(new Size(10,10))
       .SetShadowOpacity(0.7)
       .SetShadowRadius(12);
```

`VisualElement.On<iOS>`方法指定仅将在 iOS 上运行此特定于平台的。 [ `VisualElement.SetIsShadowEnabled` ](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.SetIsShadowEnabled(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement},System.Boolean))方法，在[ `Xamarin.Forms.PlatformConfiguration.iOSSpecific` ](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific)命名空间，用于控制是否在启用投影`VisualElement`。 此外，可以调用以下方法来控制投影：

- [`SetShadowColor`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.SetShadowColor(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement},Xamarin.Forms.Color)) -设置投影的颜色。 默认颜色[ `Color.Default` ](xref:Xamarin.Forms.Color.Default*)。
- [`SetShadowOffset`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.SetShadowOffset(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement},Xamarin.Forms.Size)) -设置投影的偏移量。 偏移量更改阴影被强制转换，并指定为方向[ `Size` ](xref:Xamarin.Forms.Size)值。 `Size`正在向左 （负值） 或向右 （正值） 的距离的第一个值和第二个值被更高版本的距离 （负值） 或下方 （正值） 结构的值以与设备无关单位表示. 此属性的默认值为 （0.0，0.0），这会导致卷影被强制转换涉及的每个方面`VisualElement`。
- [`SetShadowOpacity`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.SetShadowOpacity(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement},System.Double)) – 要在范围 0.0 （透明） 到 1.0 （不透明） 的值设置投影的不透明度。 默认不透明度值为 0.5。
- [`SetShadowRadius`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.SetShadowRadius(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement},System.Double)) – 设置用于呈现阴影的模糊半径。 默认半径值为 10.0。

> [!NOTE]
> 可以通过调用查询投影的状态[ `GetIsShadowEnabled` ](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.GetIsShadowEnabled(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement}))， [ `GetShadowColor` ](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.GetShadowColor(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement}))， [ `GetShadowOffset` ](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.GetShadowOffset(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement}))， [ `GetShadowOpacity` ](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.GetShadowOpacity(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement}))，并[ `GetShadowRadius` ](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.VisualElement.GetShadowRadius(Xamarin.Forms.IPlatformElementConfiguration{Xamarin.Forms.PlatformConfiguration.iOS,Xamarin.Forms.VisualElement}))方法。

结果是，可以在启用投影[ `VisualElement` ](xref:Xamarin.Forms.VisualElement):

![](drop-shadow-images/drop-shadow.png "已启用投影")

## <a name="related-links"></a>相关链接

- [PlatformSpecifics （示例）](https://developer.xamarin.com/samples/xamarin-forms/UserInterface/PlatformSpecifics/)
- [创建平台特定信息](~/xamarin-forms/platform/platform-specifics/index.md#creating-platform-specifics)
- [iOSSpecific API](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific)
