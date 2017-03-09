---
title: "MarkupCompilePass1 Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "converting XAML to binary format [WPF MSBuild]"
  - "MarkupCompilePass1 task [WPF MSBuild], parameters"
  - "converting XAML projects to compiled binary format [WPF MSBuild]"
  - "MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format"
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MarkupCompilePass1 Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 工作會將不可當地語系化的[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 專案檔轉換成編譯的二進位格式。  
  
## 工作參數  
  
|參數|描述|  
|--------|--------|  
|`AllGeneratedFiles`|選擇性 **ITaskItem\[\]** 輸出參數。<br /><br /> 包含 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 工作產生的完整檔案清單。|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|選擇性 **Boolean** 參數。<br /><br /> 指定是否要在另外的 <xref:System.AppDomain> 執行工作。  如果這個參數傳回 **false**，表示工作會在與 [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] 相同的 <xref:System.AppDomain> 中執行，執行的速度會較快。  如果參數傳回 **true**，表示會在與 [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] 不同的 <xref:System.AppDomain> 中執行，執行的速度會較慢。|  
|`ApplicationMarkup`|選擇性 **ITaskItem\[\]** 參數。<br /><br /> 指定應用程式定義 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案的名稱。|  
|`AssembliesGeneratedDuringBuild`|選擇性 **String\[\]** 參數。<br /><br /> 指定在建置程序期間變更之組件的參考。  例如，[!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] 方案所包含的專案參考另一個專案的編譯輸出。  在此情況下，第二個專案的編譯輸出就可以加入到 **AssembliesGeneratedDuringBuild** 參數。<br /><br /> 注意：**AssembliesGeneratedDuringBuild** 參數必須包含建置方案產生之完整組件集合的參考。|  
|`AssemblyName`|必要的 **String** 參數。<br /><br /> 指定專案所產生組件的簡短名稱。  例如，如果專案產生名為 **WinExeAssembly.exe** 的 [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 可執行檔，**AssemblyName** 參數的值就是 **WinExeAssembly**。|  
|`AssemblyPublicKeyToken`|選擇性 **String** 參數。<br /><br /> 指定組件的公開金鑰語彙基元。|  
|`AssemblyVersion`|選擇性 **String** 參數。<br /><br /> 指定組件的版本號碼|  
|`ContentFiles`|選擇性 **ITaskItem\[\]** 參數。<br /><br /> 指定鬆散內容檔案的清單。|  
|`DefineConstants`|選擇性 **String** 參數。<br /><br /> 指定保留 **DefineConstants** 的目前値，  這會影響目標組件的產生；如果參數變更，目標組件中的公用 API 可能會變更，而參考區域型別之 [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] 檔案的編譯可能會受到影響。|  
|`ExtraBuildControlFiles`|選擇性 **ITaskItem\[\]** 參數。<br /><br /> 指定檔案清單，以控制是否要在 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 工作重新執行時觸發重建；如果其中一個檔案變更，就會觸發重建。|  
|`GeneratedBamlFiles`|選擇性 **ITaskItem\[\]** 輸出參數。<br /><br /> 包含產生的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案清單。|  
|`GeneratedCodeFiles`|選擇性 **ITaskItem\[\]** 輸出參數。<br /><br /> 包含產生的 Managed 程式碼檔案。|  
|`GeneratedLocalizationFiles`|選擇性 **ITaskItem\[\]** 輸出參數。<br /><br /> 包含為每個可當地語系化的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案產生的當地語系化檔案清單。|  
|`HostInBrowser`|選擇性 **String** 參數。<br /><br /> 指定產生的組件是否為 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]。  有效選項為 **true** 和 **false**。  如果為 **true**，產生的程式碼就會支援瀏覽器裝載。|  
|`KnownReferencePaths`|選擇性 **String\[\]** 參數。<br /><br /> 指定在建置程序期間不會變更之組件的參考。  其中包含位於[!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)]、[!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] 安裝目錄等的組件。|  
|`Language`|必要的 **String** 參數。<br /><br /> 指定編譯器支援的 Managed 語言。  有效的選項是 **C\#**，  **VB**，  **JScript**，以及  **C\+\+**。|  
|`LanguageSourceExtension`|選擇性 **String** 參數。<br /><br /> 指定附加到所產生 Managed 程式碼檔案副檔名的副檔名：<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> 如果 **LanguageSourceExtension** 參數沒有設定特定值，則會使用語言的預設原始程式檔副檔名：[!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)] 為 **.vb**，[!INCLUDE[TLA#tla_cshrp](../msbuild/includes/tlasharptla_cshrp_md.md)] 為 **.csharp**。|  
|`LocalizationDirectivesToLocFile`|選擇性 **String** 參數。<br /><br /> 指定如何產生每個 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 原始程式檔的當地語系化資訊。  有效選項包括 **None**、**CommentsOnly** 和 **All**。|  
|`OutputPath`|必要的 **String** 參數。<br /><br /> 指定所產生的 Managed 程式碼檔案和 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案要在哪個目錄中產生。|  
|`OutputType`|必要的 **String** 參數。<br /><br /> 指定專案所產生組件的類型。  有效選項包括 **winexe**、**exe**、**library** 和 **netmodule**。|  
|`PageMarkup`|選擇性 **ITaskItem\[\]** 參數。<br /><br /> 指定要處理的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案清單。|  
|`References`|選擇性 **ITaskItem\[\]** 參數。<br /><br /> 指定檔案對包含 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案所用型別之組件的參考清單。|  
|`RequirePass2ForMainAssembly`|選擇性 **Boolean** 輸出參數。<br /><br /> 表示專案是否包含不可當地語系化的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案，這些檔案參考內嵌到主要組件的區域型別。|  
|`RequirePass2ForSatelliteAssembly`|選擇性 **Boolean** 輸出參數。<br /><br /> 表示專案是否包含可當地語系化的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案 \(這些檔案參考內嵌到主要組件的區域型別\)。|  
|`RootNamespace`|選擇性 **String** 參數。<br /><br /> 指定專案中類別的根命名空間。  若對應的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案沒有 `x:Class` 屬性，則產生的 Managed 程式碼檔案也會使用 **RootNamespace** 做為預設命名空間。|  
|`SourceCodeFiles`|選擇性 **ITaskItem\[\]** 參數。<br /><br /> 指定目前專案的程式碼檔案清單。  此清單不包含產生的語言特定 Managed 程式碼檔案。|  
|`UICulture`|選擇性 **String** 參數。<br /><br /> 指定 UI 文化特性 \(Culture\) 的附屬組件，產生的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案會內嵌到該附屬組件。  如果沒有設定 **UICulture**，產生的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案會內嵌到主要組件。|  
|`XAMLDebuggingInformation`|選擇性 **Boolean** 參數。<br /><br /> 若為 **true**，表示會產生診斷資訊，並包含在編譯的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 中，以協助偵錯。|  
  
## 備註  
 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 工作通常會將 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 編譯成二進位格式並產生程式碼檔案。  如果 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案參考相同專案中定義的型別，編譯成二進位格式的作業會由 **MarkupCompilePass1** 延後到第二次標記編譯傳遞 \(**MarkupCompilePass2**\)。  這類檔案之所以必須延後編譯，是因為它們必須先等參考的區域定義型別編譯完成。  不過，如果 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案有 `x:Class` 屬性，<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 會為它產生語言特定程式碼檔案。  
  
 如果 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案包含使用 `x:Uid` 屬性的項目，表示此檔案可當地語系化：  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 當 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案宣告 [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)] 命名空間，而這個命名空間使用 `clr-namespace` 值參考目前專案中的命名空間時，表示此檔案參考區域定義型別：  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"  
    >  
    <Grid>  
      <Grid.Resources>  
        <localNameSpace:LocalType x:Key="localType" />  
      </Grid.Resources>  
      ...  
    </Grid>  
</Page>  
```  
  
 如果任何 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案可當地語系化，或參考區域定義型別，就需要第二次標記編譯傳遞，這需要先執行 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)，再執行 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)。  
  
## 範例  
 下列範例顯示如何將三個 `Page` [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案轉換成二進位格式檔案。  `Page1` 包含型別 `Class1` 的參考，由於這個型別位於專案的根命名空間，因此在這次標記編譯傳遞不會轉換成二進位格式檔案。  相反地，[GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) 會先執行，接著再執行 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass1Task">  
    <MarkupCompilePass1   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      ApplicationMarkup="App.xaml"  
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"  
      SourceCodeFiles="Class1.cs"  
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
  </Target>  
</Project>  
```  
  
## 請參閱  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [建置 WPF 應用程式 \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [WPF XAML 瀏覽器應用程式概觀](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)