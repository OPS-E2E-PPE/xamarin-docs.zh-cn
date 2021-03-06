---
title: Xamarin.Forms 之间导航布局
description: 默认情况下，CollectionView 将各个项显示垂直列表中。 但是，可以指定垂直和水平列表和网格。
ms.prod: xamarin
ms.assetid: 5FE78207-1BD6-4706-91EF-B13932321FC9
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 07/01/2019
ms.openlocfilehash: 786cea04718022847bba2ecffed8f377dd49bd8b
ms.sourcegitcommit: 0fd04ea3af7d6a6d6086525306523a5296eec0df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512797"
---
# <a name="xamarinforms-collectionview-layout"></a>Xamarin.Forms 之间导航布局

![](~/media/shared/preview.png "此 API 当前为预发布版本")

[![下载示例](~/media/shared/download.png)下载示例](https://github.com/xamarin/xamarin-forms-samples/tree/master/UserInterface/CollectionViewDemos/)

[`CollectionView`](xref:Xamarin.Forms.CollectionView) 定义用于控制布局的以下属性：

- [`ItemsLayout`](xref:Xamarin.Forms.ItemsLayout)类型的[ `IItemsLayout` ](xref:Xamarin.Forms.IItemsLayout)，指定要使用的布局。
- [`ItemSizingStrategy`](xref:Xamarin.Forms.ItemsView.ItemSizingStrategy)类型的[ `ItemSizingStrategy` ](xref:Xamarin.Forms.ItemSizingStrategy)，指定要使用的项度量值策略。

这些属性受到[ `BindableProperty` ](xref:Xamarin.Forms.BindableProperty)对象，这意味着，属性可以是数据绑定的目标。

默认情况下[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)将各个项显示垂直列表中。 但是，可以使用任何下列布局：

- 垂直列表 – 垂直增长时添加新项目时的单个列列表。
- 水平列表-水平变宽，添加新项目时的单个行列表。
- 垂直网格 – 垂直增长时添加新项目时的多列网格。
- 水平网格 – 水平变宽，添加新项目时的多行网格。

可以通过设置指定这些布局[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)属性类，该类派生自[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsLayout)类。 此类定义以下属性：

- [`Orientation`](xref:Xamarin.Forms.ItemsLayout.Orientation)类型的[ `ItemsLayoutOrientation` ](xref:Xamarin.Forms.ItemsLayoutOrientation)，在其中指定的方向[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)扩展添加项目时。
- [`SnapPointsAlignment`](xref:Xamarin.Forms.ItemsLayout.SnapPointsAlignment)类型的[ `SnapPointsAlignment` ](xref:Xamarin.Forms.SnapPointsAlignment)，指定管理单元点包含项的对齐方式。
- [`SnapPointsType`](xref:Xamarin.Forms.ItemsLayout.SnapPointsType)类型的[ `SnapPointsType` ](xref:Xamarin.Forms.SnapPointsType)，滚动时显示指定的管理点的行为。

这些属性受到[ `BindableProperty` ](xref:Xamarin.Forms.BindableProperty)对象，这意味着，属性可以是数据绑定的目标。 有关管理点的详细信息，请参阅[对齐点](scrolling.md#snap-points)中[Xamarin.Forms CollectionView 滚动](scrolling.md)指南。

[ `ItemsLayoutOrientation` ](xref:Xamarin.Forms.ItemsLayoutOrientation)枚举定义以下成员：

- `Vertical` 指示[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)添加项目时，将垂直展开。
- `Horizontal` 指示[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)添加项目时，将水平展开。

[ `ListItemsLayout` ](xref:Xamarin.Forms.ListItemsLayout)类继承自[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsLayout)类，并定义`ItemSpacing`类型的属性， `double`，表示每个项周围的空白区域。 此属性的默认值为 0，并且其值始终必须大于或等于 0。 `ListItemsLayout`类还定义了静态`Vertical`和`Horizontal`成员。 这些成员可用于分别创建垂直或水平列表。 或者，`ListItemsLayout`可以创建对象，指定[ `ItemsLayoutOrientation` ](xref:Xamarin.Forms.ItemsLayoutOrientation)作为自变量的枚举成员。

[ `GridItemsLayout` ](xref:Xamarin.Forms.GridItemsLayout)类继承自[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsLayout)类，并定义以下属性：

- `VerticalItemSpacing`类型的`double`，表示每个项周围的垂直空白区域。 此属性的默认值为 0，并且其值始终必须大于或等于 0。
- `HorizontalItemSpacing`类型的`double`，表示每个项周围的水平空白区域。 此属性的默认值为 0，并且其值始终必须大于或等于 0。
- `Span`类型的`int`，它表示要在网格中显示的行或列数。 此属性的默认值为 1，且其值必须始终为大于或等于 1。

这些属性受到[ `BindableProperty` ](xref:Xamarin.Forms.BindableProperty)对象，这意味着，属性可以是数据绑定的目标。

> [!NOTE]
> [`CollectionView`](xref:Xamarin.Forms.CollectionView) 使用本机布局引擎执行布局。

## <a name="vertical-list"></a>垂直列表

默认情况下[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)将各个项显示垂直列表布局中。 因此，不需要设置[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)属性，以使用此布局：

```xaml
<CollectionView ItemsSource="{Binding Monkeys}">
    <CollectionView.ItemTemplate>
        <DataTemplate>
            <Grid Padding="10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <Image Grid.RowSpan="2"
                       Source="{Binding ImageUrl}"
                       Aspect="AspectFill"
                       HeightRequest="60"
                       WidthRequest="60" />
                <Label Grid.Column="1"
                       Text="{Binding Name}"
                       FontAttributes="Bold" />
                <Label Grid.Row="1"
                       Grid.Column="1"
                       Text="{Binding Location}"
                       FontAttributes="Italic"
                       VerticalOptions="End" />
            </Grid>
        </DataTemplate>
    </CollectionView.ItemTemplate>
</CollectionView>
```

但是，出于完整性的考虑， [ `CollectionView` ](xref:Xamarin.Forms.CollectionView)可以设置为各个项显示垂直列表中，通过设置其[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)属性设置为`VerticalList`:

```xaml
<CollectionView ItemsSource="{Binding Monkeys}"
                ItemsLayout="VerticalList">
    ...
</CollectionView>
```

或者，也可以通过设置[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)指向的对象的属性[ `ListItemsLayout` ](xref:Xamarin.Forms.ListItemsLayout)类中，指定`Vertical` [ `ItemsLayoutOrientation`](xref:Xamarin.Forms.ItemsLayoutOrientation)作为自变量的枚举成员：

```xaml
<CollectionView ItemsSource="{Binding Monkeys}">
    <CollectionView.ItemsLayout>
        <ListItemsLayout>
            <x:Arguments>
                <ItemsLayoutOrientation>Vertical</ItemsLayoutOrientation>    
            </x:Arguments>
        </ListItemsLayout>
    </CollectionView.ItemsLayout>
    ...
</CollectionView>
```

等效 C# 代码如下：

```csharp
CollectionView collectionView = new CollectionView
{
    ...
    ItemsLayout = ListItemsLayout.Vertical
};
```

这会导致单个列列表，如添加新项垂直增长时：

[![CollectionView 垂直列表布局，在 iOS 和 Android 上的屏幕截图](layout-images/vertical-list.png "CollectionView 垂直列表布局")](layout-images/vertical-list-large.png#lightbox "CollectionView 垂直列表布局")

## <a name="horizontal-list"></a>水平列表

[`CollectionView`](xref:Xamarin.Forms.CollectionView) 可以通过设置水平列表中显示其项及其[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)属性设置为`HorizontalList`:

```xaml
<CollectionView ItemsSource="{Binding Monkeys}"
                ItemsLayout="HorizontalList">
    <CollectionView.ItemTemplate>
        <DataTemplate>
            <Grid Padding="10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="35" />
                    <RowDefinition Height="35" />
                </Grid.RowDefinitions>
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="70" />
                    <ColumnDefinition Width="140" />
                </Grid.ColumnDefinitions>
                <Image Grid.RowSpan="2"
                       Source="{Binding ImageUrl}"
                       Aspect="AspectFill"
                       HeightRequest="60"
                       WidthRequest="60" />
                <Label Grid.Column="1"
                       Text="{Binding Name}"
                       FontAttributes="Bold"
                       LineBreakMode="TailTruncation" />
                <Label Grid.Row="1"
                       Grid.Column="1"
                       Text="{Binding Location}"
                       LineBreakMode="TailTruncation"
                       FontAttributes="Italic"
                       VerticalOptions="End" />
            </Grid>
        </DataTemplate>
    </CollectionView.ItemTemplate>
</CollectionView>
```

或者，也可以通过设置[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)属性设置为[ `ListItemsLayout` ](xref:Xamarin.Forms.ListItemsLayout)对象，指定`Horizontal` [ `ItemsLayoutOrientation` ](xref:Xamarin.Forms.ItemsLayoutOrientation)作为参数的枚举成员：

```xaml
<CollectionView ItemsSource="{Binding Monkeys}">
    <CollectionView.ItemsLayout>
        <ListItemsLayout>
            <x:Arguments>
                <ItemsLayoutOrientation>Horizontal</ItemsLayoutOrientation>    
            </x:Arguments>
        </ListItemsLayout>
    </CollectionView.ItemsLayout>
    ...
</CollectionView>
```

等效 C# 代码如下：

```csharp
CollectionView collectionView = new CollectionView
{
    ...
    ItemsLayout = ListItemsLayout.Horizontal
};
```

这会导致单个行列表，水平变宽，如添加新项：

[![CollectionView 水平列表布局，在 iOS 和 Android 上的屏幕截图](layout-images/horizontal-list.png "CollectionView 水平列表布局")](layout-images/horizontal-list-large.png#lightbox "CollectionView 水平列表布局")

## <a name="vertical-grid"></a>垂直网格

[`CollectionView`](xref:Xamarin.Forms.CollectionView) 可以通过设置垂直网格中显示其项及其[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)属性设置为[ `GridItemsLayout` ](xref:Xamarin.Forms.GridItemsLayout)对象，其[ `Orientation` ](xref:Xamarin.Forms.ItemsLayout.Orientation)属性设置为`Vertical`:

```xaml
<CollectionView ItemsSource="{Binding Monkeys}">
    <CollectionView.ItemsLayout>
       <GridItemsLayout Orientation="Vertical"
                        Span="2" />
    </CollectionView.ItemsLayout>
    <CollectionView.ItemTemplate>
        <DataTemplate>
            <Grid Padding="10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="35" />
                    <RowDefinition Height="35" />
                </Grid.RowDefinitions>
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="70" />
                    <ColumnDefinition Width="80" />
                </Grid.ColumnDefinitions>
                <Image Grid.RowSpan="2"
                       Source="{Binding ImageUrl}"
                       Aspect="AspectFill"
                       HeightRequest="60"
                       WidthRequest="60" />
                <Label Grid.Column="1"
                       Text="{Binding Name}"
                       FontAttributes="Bold"
                       LineBreakMode="TailTruncation" />
                <Label Grid.Row="1"
                       Grid.Column="1"
                       Text="{Binding Location}"
                       LineBreakMode="TailTruncation"
                       FontAttributes="Italic"
                       VerticalOptions="End" />
            </Grid>
        </DataTemplate>
    </CollectionView.ItemTemplate>
</CollectionView>
```

等效 C# 代码如下：

```csharp
CollectionView collectionView = new CollectionView
{
    ...
    ItemsLayout = new GridItemsLayout(2, ItemsLayoutOrientation.Vertical)
};
```

默认情况下，垂直[ `GridItemsLayout` ](xref:Xamarin.Forms.GridItemsLayout)将在单个列中显示项。 但是，此示例设置`GridItemsLayout.Span`属性设置为 2。 这会导致两个列网格，如添加新项垂直增长时：

[![CollectionView 垂直网格布局，在 iOS 和 Android 上的屏幕截图](layout-images/vertical-grid.png "CollectionView 垂直网格布局")](layout-images/vertical-grid-large.png#lightbox "CollectionView 垂直网格布局")

## <a name="horizontal-grid"></a>水平网格

[`CollectionView`](xref:Xamarin.Forms.CollectionView) 可以通过设置水平网格中显示其项及其[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)属性设置为[ `GridItemsLayout` ](xref:Xamarin.Forms.GridItemsLayout)对象，其[`Orientation` ](xref:Xamarin.Forms.ItemsLayout.Orientation)属性设置为`Horizontal`:

```xaml
<CollectionView ItemsSource="{Binding Monkeys}">
    <CollectionView.ItemsLayout>
       <GridItemsLayout Orientation="Horizontal"
                        Span="4" />
    </CollectionView.ItemsLayout>
    <CollectionView.ItemTemplate>
        <DataTemplate>
            <Grid Padding="10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="35" />
                    <RowDefinition Height="35" />
                </Grid.RowDefinitions>
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="70" />
                    <ColumnDefinition Width="140" />
                </Grid.ColumnDefinitions>
                <Image Grid.RowSpan="2"
                       Source="{Binding ImageUrl}"
                       Aspect="AspectFill"
                       HeightRequest="60"
                       WidthRequest="60" />
                <Label Grid.Column="1"
                       Text="{Binding Name}"
                       FontAttributes="Bold"
                       LineBreakMode="TailTruncation" />
                <Label Grid.Row="1"
                       Grid.Column="1"
                       Text="{Binding Location}"
                       LineBreakMode="TailTruncation"
                       FontAttributes="Italic"
                       VerticalOptions="End" />
            </Grid>
        </DataTemplate>
    </CollectionView.ItemTemplate>
</CollectionView>
```

等效 C# 代码如下：

```csharp
CollectionView collectionView = new CollectionView
{
    ...
    ItemsLayout = new GridItemsLayout(4, ItemsLayoutOrientation.Horizontal)
};
```

默认情况下，水平[ `GridItemsLayout` ](xref:Xamarin.Forms.GridItemsLayout)将在单个行中显示项。 但是，此示例设置`GridItemsLayout.Span`属性设置为 4。 这会导致水平变宽，添加新项目时的四行网格：

[![CollectionView 水平网格布局，在 iOS 和 Android 上的屏幕截图](layout-images/horizontal-grid.png "CollectionView 水平网格布局")](layout-images/horizontal-grid-large.png#lightbox "CollectionView 水平网格布局")

## <a name="item-spacing"></a>项间距

默认情况下，每个项目中[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)不具有在其周围的任意空白区域。 可以通过设置属性上使用的项布局更改此行为`CollectionView`。

当[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)设置其[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)属性设置为[ `ListItemsLayout` ](xref:Xamarin.Forms.ListItemsLayout)对象，`ListItemsLayout.ItemSpacing`属性设置为`double`表示每个项周围的空白区域的值：

```xaml
<CollectionView ItemsSource="{Binding Monkeys}">
    <CollectionView.ItemsLayout>
        <ListItemsLayout ItemSpacing="20">
            <x:Arguments>
                <ItemsLayoutOrientation>Vertical</ItemsLayoutOrientation>    
            </x:Arguments>
        </ListItemsLayout>
    </CollectionView.ItemsLayout>
    ...
</CollectionView>
```

> [!NOTE]
> `ListItemsLayout.ItemSpacing`属性验证回调集有，这可确保该属性的值始终是大于或等于 0。

等效 C# 代码如下：

```csharp
CollectionView collectionView = new CollectionView
{
    ...
    ItemsLayout = new ListItemsLayout(ItemsLayoutOrientation.Vertical)
    {
        ItemSpacing = 20
    }
};
```

此代码会导致，具有 20 每个项周围的间距的垂直单列列表：

[![项间距，iOS 和 Android 上使用 CollectionView 的屏幕截图](layout-images/vertical-list-spacing.png "CollectionView 项间距")](layout-images/vertical-list-spacing-large.png#lightbox "之间导航项间距")

当[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)设置其[ `ItemsLayout` ](xref:Xamarin.Forms.ItemsView.ItemsLayout)属性设置为[ `GridItemsLayout` ](xref:Xamarin.Forms.GridItemsLayout)对象，`GridItemsLayout.VerticalItemSpacing`和`GridItemsLayout.HorizontalItemSpacing`属性可以是设置为`double`表示每个项周围的空白垂直和水平方向的值：

```xaml
<CollectionView ItemsSource="{Binding Monkeys}">
    <CollectionView.ItemsLayout>
       <GridItemsLayout Orientation="Vertical"
                        Span="2"
                        VerticalItemSpacing="20"
                        HorizontalItemSpacing="30" />
    </CollectionView.ItemsLayout>
    ...
</CollectionView>
```

> [!NOTE]
> `GridItemsLayout.VerticalItemSpacing`和`GridItemsLayout.HorizontalItemSpacing`属性已设置，它们可确保的属性的值始终是大于或等于 0 的验证回叫。

等效 C# 代码如下：

```csharp
CollectionView collectionView = new CollectionView
{
    ...
    ItemsLayout = new GridItemsLayout(2, ItemsLayoutOrientation.Vertical)
    {
        VerticalItemSpacing = 20,
        HorizontalItemSpacing = 30
    }
};
```

此代码会导致垂直的两列式网格，具有垂直间距的每个项周围的 20 和 30，每个项周围的水平间距：

[![项间距，iOS 和 Android 上使用 CollectionView 的屏幕截图](layout-images/vertical-grid-spacing.png "CollectionView 项间距")](layout-images/vertical-grid-spacing-large.png#lightbox "之间导航项间距")

## <a name="item-sizing"></a>项大小调整

默认情况下，每个项目中[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)分别是测量和调整大小、 提供程序中的 UI 元素[ `DataTemplate` ](xref:Xamarin.Forms.DataTemplate)未指定固定的大小。 指定此行为，可以更改[ `CollectionView.ItemSizingStrategy` ](xref:Xamarin.Forms.ItemsView.ItemSizingStrategy)属性值。 此属性的值可以设置为之一[ `ItemSizingStrategy` ](xref:Xamarin.Forms.ItemSizingStrategy)枚举成员：

- `MeasureAllItems` – 每个项分别进行测量。 这是默认值。
- `MeasureFirstItem` – 仅第一项度量单位，与所提供的第一项的大小相同的所有后续项。

> [!IMPORTANT]
> `MeasureFirstItem`大小调整策略将导致更高的性能时在其中的项大小应在所有项之间是一致的情况下使用。

下面的代码示例显示了设置[ `ItemSizingStrategy` ](xref:Xamarin.Forms.ItemsView.ItemSizingStrategy)属性：

```xaml
<CollectionView ...
                ItemSizingStrategy="MeasureFirstItem">
    ...
</CollectionView>
```

等效 C# 代码如下：

```csharp
CollectionView collectionView = new CollectionView
{
    ...
    ItemSizingStrategy = ItemSizingStrategy.MeasureFirstItem
};
```

## <a name="dynamic-resizing-of-items"></a>动态调整大小的项

中的项[ `CollectionView` ](xref:Xamarin.Forms.CollectionView)可以动态调整大小在运行时通过更改布局相关属性中的元素[ `DataTemplate` ](xref:Xamarin.Forms.DataTemplate)。 例如，下面的代码示例中更改[ `HeightRequest` ](xref:Xamarin.Forms.VisualElement.HeightRequest)并[ `WidthRequest` ](xref:Xamarin.Forms.VisualElement.WidthRequest)属性的[ `Image` ](xref:Xamarin.Forms.Image)对象：

```csharp
void OnImageTapped(object sender, EventArgs e)
{
    Image image = sender as Image;
    image.HeightRequest = image.WidthRequest = image.HeightRequest.Equals(60) ? 100 : 60;
}
```

`OnImageTapped`事件处理程序执行以响应[ `Image` ](xref:Xamarin.Forms.Image)对象被点击，并更改图像的尺寸，以便更轻松地查看：

[![与动态项大小调整，iOS 和 Android 上 CollectionView 的屏幕截图](layout-images/runtime-resizing.png "CollectionView 动态项目大小调整")](layout-images/runtime-resizing-large.png#lightbox "CollectionView 动态项目大小调整")

## <a name="right-to-left-layout"></a>从右到左布局

[`CollectionView`](xref:Xamarin.Forms.CollectionView) 从右到左流动方向中的其内容的布局可能通过设置其[ `FlowDirection` ](xref:Xamarin.Forms.VisualElement.FlowDirection)属性设置为[ `RightToLeft` ](xref:Xamarin.Forms.FlowDirection.RightToLeft)。 但是，`FlowDirection`属性应在理想情况下设置页或根布局，这会导致页上或根布局中的所有元素，以响应流方向：

```xaml
<?xml version="1.0" encoding="UTF-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="CollectionViewDemos.Views.VerticalListFlowDirectionPage"
             Title="Vertical list (RTL FlowDirection)"
             FlowDirection="RightToLeft">
    <StackLayout Margin="20">
        <CollectionView ItemsSource="{Binding Monkeys}">
            ...
        </CollectionView>
    </StackLayout>
</ContentPage>
```

默认值[ `FlowDirection` ](xref:Xamarin.Forms.VisualElement.FlowDirection)使用的父元素[ `MatchParent` ](xref:Xamarin.Forms.FlowDirection.MatchParent)。 因此， [ `CollectionView` ](xref:Xamarin.Forms.CollectionView)继承`FlowDirection`属性值从[ `StackLayout` ](xref:Xamarin.Forms.StackLayout)，其中又继承`FlowDirection`属性值从[`ContentPage`](xref:Xamarin.Forms.ContentPage). 这会导致从右到左布局中的以下屏幕截图所示：

[![CollectionView 垂直列表中从右到左布局，在 iOS 和 Android 上的屏幕截图](layout-images/vertical-list-rtl.png "CollectionView 垂直列表中从右到左布局")](layout-images/vertical-list-rtl-large.png#lightbox "CollectionView 从右到左垂直列表布局")

有关流方向的详细信息，请参阅[从右到左本地化](~/xamarin-forms/app-fundamentals/localization/right-to-left.md)。

## <a name="related-links"></a>相关链接

- [CollectionView （示例）](https://github.com/xamarin/xamarin-forms-samples/tree/master/UserInterface/CollectionViewDemos/)
- [从右到左本地化](~/xamarin-forms/app-fundamentals/localization/right-to-left.md)
- [Xamarin.Forms CollectionView 滚动](scrolling.md)
