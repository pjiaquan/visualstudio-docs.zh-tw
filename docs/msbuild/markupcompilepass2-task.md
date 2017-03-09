---
title: "MarkupCompilePass2 Task | Microsoft Docs"
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
  - "performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task"
  - "MarkupCompilePass2 task [WPF MSBuild]"
  - "MarkupCompilePass2 task [WPF MSBuild], parameters"
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MarkupCompilePass2 Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 工作會對參考相同專案中型別的[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 檔案執行第二次傳遞標記編譯。  
  
## 工作參數  
  
|參數|描述|  
|--------|--------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|選擇性 **Boolean** 參數。<br /><br /> 指定是否要在另外的 <xref:System.AppDomain> 執行工作。  如果這個參數傳回 **false**，表示工作會在與 [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] 相同的 <xref:System.AppDomain> 中執行，執行的速度會較快。  如果參數傳回 **true**，表示會在與 [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] 不同的 <xref:System.AppDomain> 中執行，執行的速度會較慢。|  
|`AssembliesGeneratedDuringBuild`|選擇性 **String\[\]** 參數。<br /><br /> 指定在建置程序期間變更之組件的參考。  例如，[!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] 方案所包含的專案參考另一個專案的編譯輸出。  在此情況下，第二個專案的編譯輸出就可以加入到 **AssembliesGeneratedDuringBuild**。<br /><br /> 注意：**AssembliesGeneratedDuringBuild** 必須包含建置方案產生之完整組件集合的參考。|  
|`AssemblyName`|必要的 **String** 參數。<br /><br /> 指定專案所產生組件的簡短名稱。  例如，如果專案產生名為 **WinExeAssembly.exe** 的 [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] 可執行檔，**AssemblyName** 參數的值就是 **WinExeAssembly**。|  
|`GeneratedBaml`|選擇性 **ITaskItem\[\]** 輸出參數。<br /><br /> 包含產生的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案清單。|  
|`KnownReferencePaths`|選擇性 **String\[\]** 參數。<br /><br /> 指定在建置程序期間不會變更之組件的參考。  其中包含位於[!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)]、[!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] 安裝目錄等的組件。|  
|`Language`|必要的 **String** 參數。<br /><br /> 指定編譯器支援的 Managed 語言。  有效的選項是 **C\#**，  **VB**，  **JScript**，以及  **C\+\+**。|  
|`LocalizationDirectivesToLocFile`|選擇性 **String** 參數。<br /><br /> 指定如何產生每個 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 原始程式檔的當地語系化資訊。  有效選項包括 **None**、**CommentsOnly** 和 **All**。|  
|`OutputPath`|必要的 **String** 參數。<br /><br /> 指定所產生的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案要在哪個目錄中產生。|  
|`OutputType`|必要的 **String** 參數。<br /><br /> 指定專案所產生組件的類型。  有效選項包括 **winexe**、**exe**、**library** 和 **netmodule**。|  
|`References`|選擇性 **ITaskItem\[\]** 參數。<br /><br /> 指定檔案對包含 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案所用型別之組件的參考清單。  其中一個參考是對 <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> 工作產生之組件的參考，此工作必須在 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 工作之前執行。|  
|`RootNamespace`|選擇性 **String** 參數。<br /><br /> 指定專案中類別的根命名空間。  若對應的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案沒有 `x:Class` 屬性，則產生的 Managed 程式碼檔案也會使用 **RootNamespace** 做為預設命名空間。|  
|`XAMLDebuggingInformation`|選擇性 **Boolean** 參數。<br /><br /> 若為 **true**，表示會產生診斷資訊，並包含在編譯的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 中，以協助偵錯。|  
  
## 備註  
 執行 **MarkupCompilePass2** 之前，您必須產生暫存組件，其中包含標記編譯傳遞延後的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案所使用的型別。  您可以執行 **GenerateTemporaryTargetAssembly** 工作來產生暫存組件。  
  
 所產生暫存組件的參考會在 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 執行時提供給它，讓編譯在第一次標記編譯傳遞延後的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案這時得以編譯成二進位格式。  
  
## 範例  
 下列範例顯示如何使用 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 工作執行第二次傳遞編譯。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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