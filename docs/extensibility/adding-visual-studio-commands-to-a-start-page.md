---
title: "將 Visual Studio 命令加入至起始頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c75d9b41d0e51d6db2e78d0afa0e1ddf37e87b8a
ms.lasthandoff: 02/22/2017

---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>將 Visual Studio 命令加入至 [開始] 頁面
當您建立自訂起始頁時，您可以新增 Visual Studio 指令。 本文件討論將 Visual Studio 命令繫結至 XAML 物件的起始頁上的不同方式。  
  
 如需 XAML 中的命令的詳細資訊，請參閱[命令概觀](http://msdn.microsoft.com/Library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>也將命令加入命令  
 [開始] 頁面中建立[建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)加入<xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>和<xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>命名空間，如下所示。</xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> </xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 從組件 Microsoft.VisualStudio.Shell.Immutable.11.0.dll Microsoft.VisualStudio.Shell 加入另一個命名空間。 （您可能需要將此組件的參考加入專案中）。  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 您可以使用`vscom:`繫結至 XAML 的 Visual Studio 命令別名控制頁面上，藉由設定<xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>屬性來控制`vscom:VSCommands.ExecuteCommand`。</xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> 然後您可以設定<xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>屬性來執行，如下列範例所示的命令名稱。</xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:`別名，這指的是 XAML 結構描述，是需要在所有命令的開頭。  
  
 您可以設定的值`Command`屬性可以存取從任何命令**命令**視窗。 如需可用命令的清單，請參閱[Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。  
  
 如果要新增的命令需要額外的參數，可以將它的值加入`CommandParameter`屬性。 個別使用空格，如下列範例所示的命令參數。  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>從命令中也呼叫擴充功能  
 您可以使用相同的語法用來呼叫其他 Visual Studio 命令，從已註冊的 VSPackages 呼叫命令。 比方說，如果已安裝的 VSPackage 新增**首頁**命令**檢視** 功能表上，您可以呼叫該命令藉由設定`CommandParameter`到`View.HomePage`。  
  
> [!NOTE]
>  如果您呼叫 VSPackage 相關聯的命令，叫用命令時必須載入封裝。  
  
## <a name="adding-commands-from-assemblies"></a>將命令加入的組件  
 若要從組件，或沒有關聯的功能表命令的 VSPackage 中存取程式碼呼叫的命令，您必須建立組件的別名，然後呼叫別名。  
  
#### <a name="to-call-a-command-from-an-assembly"></a>若要命令呼叫的組件  
  
1.  您在方案中加入組件的參考。  
  
2.  StartPage.xaml 檔案的頂端，加入命名空間指示詞的組件，如下列範例所示。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  叫用該命令，藉由設定`Command`XAML 物件，如下列範例所示的屬性。  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  您必須複製組件，，然後將它貼...\\ *Visual Studio 安裝資料夾*\Common7\IDE\PrivateAssemblies\ 以確定會在呼叫之前載入。  
  
## <a name="adding-commands-with-the-dte-object"></a>將命令加入與 DTE 物件  
 您可以從 [開始] 頁面上，在標記和程式碼中存取 DTE 物件。  
  
 在標記中，您可以存取它使用[繫結標記延伸](http://msdn.microsoft.com/Library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63)語法來呼叫<xref:EnvDTE.DTE>物件。</xref:EnvDTE.DTE> 您可以使用這種方法來繫結至簡單的屬性，例如傳回的集合，但您無法繫結至方法或服務。 下列範例所示<xref:System.Windows.Controls.TextBlock>繫結至控制項<xref:EnvDTE._DTE.Name%2A>屬性，以及<xref:System.Windows.Controls.ListBox>列舉的控制項<xref:EnvDTE.Window.Caption%2A>屬性所傳回之集合的<xref:EnvDTE._DTE.Windows%2A>屬性。</xref:EnvDTE._DTE.Windows%2A> </xref:EnvDTE.Window.Caption%2A> </xref:System.Windows.Controls.ListBox> </xref:EnvDTE._DTE.Name%2A> </xref:System.Windows.Controls.TextBlock>  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 如需範例，請參閱[逐步解說︰ 入門 頁面上儲存使用者設定](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將使用者控制項加入至 [開始] 頁面](../extensibility/adding-user-control-to-the-start-page.md)
