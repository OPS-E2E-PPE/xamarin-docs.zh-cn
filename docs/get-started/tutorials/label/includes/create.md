---
ms.openlocfilehash: ec74a049adaa72010bf0566691e4d1f066058d4a
ms.sourcegitcommit: a153623a69b5cb125f672df8007838afa32e9edf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2019
ms.locfileid: "67277112"
---
# <a name="visual-studiotabvswin"></a>[Visual Studio](#tab/vswin)

若要完成本教程，应使用 Visual Studio 2019（最新版本），且安装了“使用 .NET 的移动开发”工作负载  。 此外，还需要一个匹配的 Mac，用于在 iOS 上生成教程应用程序。 有关安装 Xamarin 平台的信息，请参阅[安装 Xamarin](~/get-started/installation/index.md)。 有关将 Visual Studio 2019 连接到 Mac 生成主机的信息，请参阅[通过“与 Mac 配对”进行 Xamarin.iOS 开发](~/ios/get-started/installation/windows/connecting-to-mac/index.md)。

1. 启动 Visual Studio，新建一个名为 LabelTutorial 的 Xamarin.Forms 空白应用  。 确保该应用使用 .NET Standard 作为共享代码机制。

    > [!IMPORTANT]
    > 本教程中的 C# 和 XAML 片段要求将解决方案命名为 LabelTutorial  。 使用不同的名称会导致：将本教程中的代码复制到解决方案中时出现生成错误。

    有关创建的 .NET Standard 库的详细信息，请参阅 [Xamarin.Forms 快速入门的深入探讨](~/get-started/first-app/index.md)中的 [Xamarin.Forms 应用程序剖析](~/get-started/first-app/index.md)。

1. 在“解决方案资源管理器”的 LabelTutorial 项目中，双击 MainPage.xaml 将其打开    。 然后在 MainPage.xaml 中，删除所有模板代码，替换为以下代码  ：

    ```xaml
    <?xml version="1.0" encoding="utf-8"?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="LabelTutorial.MainPage">
       <StackLayout Margin="20,35,20,20">
            <Label Text="Welcome to Xamarin.Forms!"
                   HorizontalOptions="Center" />
       </StackLayout>
    </ContentPage>
    ```

    此代码以声明方式定义页面的用户界面，该界面由 [`StackLayout`](xref:Xamarin.Forms.StackLayout) 中的 [`Label`](xref:Xamarin.Forms.Label) 组成。 [`Label.Text`](xref:Xamarin.Forms.Button.Text) 属性指定显示的文本，[`HorizontalOptions`](xref:Xamarin.Forms.View.HorizontalOptions) 属性指定文本将水平居中。

1. 在 Visual Studio 工具栏中，按“开始”按钮（类似“播放”按钮的三角形按钮），启动所选远程 iOS 模拟器或 Android Emulator 内的应用程序  ：

    [![iOS 和 Android 上居中标签的屏幕截图](../images/create-label.png "居中标签")](../images/create-label-large.png#lightbox "A centered Label")

# <a name="visual-studio-for-mactabvsmac"></a>[Visual Studio for Mac](#tab/vsmac)

若要完成本教程，应使用 Visual Studio for Mac（最新版），且安装了 iOS 和 Android 平台支持。 此外，还需要 Xcode（最新版）。 有关安装 Xamarin 平台的详细信息，请参阅[安装 Xamarin](~/get-started/installation/index.md)。

1. 启动 Visual Studio for Mac，新建名为 LabelTutorial 的 Xamarin.Forms 空白应用  。 确保该应用使用 .NET Standard 作为共享代码机制。

    > [!IMPORTANT]
    > 本教程中的 C# 和 XAML 片段要求将解决方案命名为 LabelTutorial  。 使用不同的名称会导致：将本教程中的代码复制到解决方案中时出现生成错误。

    有关创建的 .NET Standard 库的详细信息，请参阅 [Xamarin.Forms 快速入门的深入探讨](~/get-started/first-app/index.md)中的 [Xamarin.Forms 应用程序剖析](~/get-started/first-app/index.md)。

1. 在“Solution Pad”的 LabelTutorial 项目中，双击 MainPage.xaml 将其打开    。 然后在 MainPage.xaml 中，删除所有模板代码，替换为以下代码  ：

    ```xaml
    <?xml version="1.0" encoding="utf-8"?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="LabelTutorial.MainPage">
       <StackLayout Margin="20,35,20,20">
            <Label Text="Welcome to Xamarin.Forms!"
                   HorizontalOptions="Center" />
       </StackLayout>
    </ContentPage>
    ```

    此代码以声明方式定义页面的用户界面，该界面由 [`StackLayout`](xref:Xamarin.Forms.StackLayout) 中的 [`Label`](xref:Xamarin.Forms.Label) 组成。 [`Label.Text`](xref:Xamarin.Forms.Button.Text) 属性指定显示的文本，[`HorizontalOptions`](xref:Xamarin.Forms.View.HorizontalOptions) 属性指定文本将水平居中。

1. 在 Visual Studio for Mac 工具栏中，按“开始”按钮（类似“播放”按钮的三角形按钮），启动所选 iOS 模拟器或 Android 模拟器内的应用程序  ：

    [![iOS 和 Android 上居中标签的屏幕截图](../images/create-label.png "居中标签")](../images/create-label-large.png#lightbox "A centered Label")
