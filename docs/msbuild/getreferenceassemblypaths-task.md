---
title: "GetReferenceAssemblyPaths Task | Microsoft Docs"
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# GetReferenceAssemblyPaths Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

傳回各種不同架構的參考組件路徑。  
  
## 參數  
 下表說明 `GetReferenceAssemblyPaths` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`ReferenceAssemblyPaths`|選擇性的 `String[]` 輸出參數。<br /><br /> 根據 `TargetFrameworkMoniker` 參數傳回路徑。  如果 `TargetFrameworkMoniker` 是 Null 或空白，則此路徑為 `String.Empty`。|  
|`FullFrameworkReferenceAssemblyPaths`|選擇性的 `String[]` 輸出參數。<br /><br /> 傳回路徑，此路徑是以 `TargetFrameworkMoniker` 參數為根據，而不考慮 Moniker 的設定檔部分。  如果 `TargetFrameworkMoniker` 是 Null 或空白，則此路徑為 `String.Empty`。|  
|`TargetFrameworkMoniker`|選擇性 `String` 參數。<br /><br /> 指定與參考組件路徑相關聯的目標 Framework Moniker。|  
|`RootPath`|選擇性 `String` 參數。<br /><br /> 指定用來產生參考組件路徑的根路徑。|  
|`BypassFrameworkInstallChecks`|選擇性 [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) 參數。<br /><br /> 如果為 `true`，則會略過 `GetReferenceAssemblyPaths` 預設執行的基本檢查，以確定已根據目標 Framework 來安裝特定執行階段 Framework。|  
|`TargetFrameworkMonikerDisplayName`|選擇性 `String` 輸出參數。<br /><br /> 指定目標 Framework Moniker 的顯示名稱。|  
  
## 備註  
 除了會有表中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)