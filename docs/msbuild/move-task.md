---
title: "Move Task | Microsoft Docs"
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
  - "MSBuild, Move task"
  - "Move task [MSBuild]"
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Move Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將檔案移至新位置。  
  
## 參數  
 下表說明 `Move` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`DestinationFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定要移動來源檔的檔案清單。  這份清單必須是一對一對應至 `SourceFiles` 參數所指定的清單。  也就是說，在 `SourceFiles` 中指定的第一個檔案，將會移動到在 `DestinationFiles` 中指定的第一個位置，其他依此類推。|  
|`DestinationFolder`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要移動檔案的目錄。|  
|`MovedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含已順利移動的項目。|  
|`OverwriteReadOnlyFiles`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，即使將檔案標記為唯讀，也會覆寫檔案。|  
|`SourceFiles`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要移動的檔案。|  
  
## 備註  
 必須指定 `DestinationFolder` 參數或 `DestinationFiles` 參數，但不是同時指定兩者。  如果同時指定兩者，工作便會失敗並會記錄一項錯誤。  
  
 除了會有表中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)