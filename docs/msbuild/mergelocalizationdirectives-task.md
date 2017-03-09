---
title: "MergeLocalizationDirectives Task | Microsoft Docs"
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
  - "localizing XAML [WPF MSBuild], moving comments and attributes to a separate file"
  - "MergeLocalizationDirectives task [WPF MSBuild], parameters"
  - "MergeLocalizationDirectives task [WPF MSBuild]"
  - "moving localization comments and attributes to a separate file [WPF MSBuild]"
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MergeLocalizationDirectives Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> 工作可將一或多個 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案的當地語系化屬性和註解合併成單一檔案，以供整個組件使用。  
  
## 工作參數  
  
|參數|描述|  
|--------|--------|  
|`GeneratedLocalizationFiles`|必要的 **ITaskItem\[\]** 參數。<br /><br /> 指定個別 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案的當地語系化指示詞檔案清單。|  
|`OutputFile`|必要的 **String** 輸出參數。<br /><br /> 指定編譯當地語系化指示詞組件的輸出路徑。|  
  
## 備註  
 您可以將當地語系化和註解加入到[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 內容。  由於 [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] 支援當地語系化，您可以取出當地語系化屬性和註解，然後與產生的組件分開，放到另外的 .loc 檔案中。  您可以使用 **LocalizationPropertyStorage** 屬性執行此動作。  如需當地語系化屬性、註解和 **LocalizationPropertyStorage** 的詳細資訊，請參閱[當地語系化屬性和註解](../Topic/Localization%20Attributes%20and%20Comments.md)。  
  
## 範例  
 下列範例會將幾個 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案的當地語系化註解合併到單一 .loc 檔案。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## 請參閱  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [建置 WPF 應用程式 \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)