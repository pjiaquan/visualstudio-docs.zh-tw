---
title: "RequiresFramework35SP1Assembly Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "RequiresFramework35SP1Assembly task [MSBuild]"
  - "MSBuild, RequiresFramework35SP1Assembly task"
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# RequiresFramework35SP1Assembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

判斷應用程式是否需要 .NET Framework 3.5 SP1。  
  
## 參數  
 下表說明 `RequiresFramework35SP1Assembly` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Assemblies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定的組件所參考的應用程式中。|  
|`CreateDesktopShortcut`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則會在安裝期間在桌面上建立捷徑圖示。|  
|`DeploymentManifestEntryPoint`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定應用程式的資訊清單檔名稱。|  
|`EntryPoint`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要於應用程式執行時所應執行的組件。|  
|`ErrorReportUrl`|選擇性 `String` 參數。<br /><br /> 指定在 ClickOnce 安裝過程所產生的對話方塊中顯示的網站。|  
|`Files`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定將在發行應用程式時部署之檔案的清單。|  
|`ReferencedAssemblies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定的組件所參考的專案中。|  
|`RequiresMinimumFramework35SP1`|選擇性 `Boolean` 輸出參數。<br /><br /> 如果為 `true`，則應用程式需要 .NET Framework 3.5 SP1。|  
|`SigningManifests`|選擇性 `Boolean` 輸出參數。<br /><br /> 如果為 `true`，則會簽署 ClickOnce 資訊清單。|  
|`SuiteName`|選擇性 `String` 參數。<br /><br /> 指定 \[**開始**\] 功能表上應用程式將會安裝在其中的資料夾名稱。|  
|`TargetFrameworkVersion`|選擇性 `String` 參數。<br /><br /> 指定此應用程式以之為設計目標的 .NET Framework 版本。|  
  
## 備註  
 除了會有表中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)