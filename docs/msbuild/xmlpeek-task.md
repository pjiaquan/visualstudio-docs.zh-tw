---
title: "XmlPeek Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "XmlPeek task [MSBuild]"
  - "MSBuild, XmlPeek task"
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XmlPeek Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

從 XML 檔案傳回 XPath 查詢所指定的值。  
  
## 參數  
 下表說明 `XmlPeek` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Namespaces`|選擇性 `String` 參數。<br /><br /> 指定 XPath 查詢前置詞的命名空間。|  
|`Query`|選擇性 `String` 參數。<br /><br /> 指定 XPath 查詢。|  
|`Result`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含此工作傳回的結果。|  
|`XmlContent`|選擇性 `String` 參數。<br /><br /> 指定為字串形式的 XML 輸入。|  
|`XmlInputPath`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定為檔案路徑形式的 XML 輸入。|  
  
## 備註  
 除了會有表中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)