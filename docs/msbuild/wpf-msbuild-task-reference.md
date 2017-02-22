---
title: "WPF MSBuild Task Reference | Microsoft Docs"
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
  - "WPF MSBuild task reference [WPF MSBuild], term/definition table"
  - "build tasks [WPF MSBuild], Microsoft build engine"
  - "build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources"
  - "WPF MSBuild task reference [WPF MSBuild]"
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WPF MSBuild Task Reference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows Presentation Foundation \(WPF\) 建置處理序會使用額外的建置工作集合以延伸 Microsoft build engine \(MSBuild\)，包括編譯標記和處理資源的工作。  
  
## 在本節中  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 對將內嵌到組件 \(Assembly\) 的一組來源資源進行分類。  如果資源沒有當地語系化，就會內嵌到主應用程式組件，否則會內嵌到附屬組件。  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 如果專案中至少有一個[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 頁面參考在該專案區域宣告的型別，就會產生組件。  產生的組件會在建置程序完成之後或失敗時移除。  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 傳回目前 [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] 執行階段的目錄。  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 將不可當地語系化的[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 專案檔轉換成編譯的二進位格式。  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 對參考相同專案中型別的[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 檔案執行第二次傳遞標記編譯。  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 將一個或多個 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案的當地語系化屬性和註解合併成單一檔案，以供整個組件使用。  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 將一種或多種資源 \(.jpg、.ico、.bmp、二進位格式的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 以及其他副檔名類型\) 內嵌到 .resources 檔案中。  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 檢查、更新或移除唯一識別項 \(UID\)，以當地語系化[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 原始程式檔包含的所有 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 項目。  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 建置 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] 專案時，將  **\<hostInBrowser \/\>** 項目加入到應用程式資訊清單 \(*projectname*.exe.manifest\)。  
  
## 請參閱  
 [MSBuild](http://msdn.microsoft.com/zh-tw/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)