---
title: "FindAppConfigFile Task | Microsoft Docs"
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
  - "FindAppConfigFile task [MSBuild]"
  - "MSBuild, FindAppConfigFile task"
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FindAppConfigFile Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在提供的清單中尋找 app.config 檔案 \(如果有的話\)。  
  
## 參數  
 下表說明 `FindAppConfigFile` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`AppConfigFile`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定清單中找到的第一個符合項目 \(如果有的話\)。|  
|`PrimaryList`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要搜尋的主要清單。|  
|`SecondaryList`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要搜尋的次要清單。|  
|`TargetPath`|必要的 `String` 參數。<br /><br /> 指定要加入做為中繼資料的值。|  
  
## 備註  
 除了會有表中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)