---
title: "XmlPoke Task | Microsoft Docs"
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
  - "XmlPoke task [MSBuild]"
  - "MSBuild, XmlPoke task"
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# XmlPoke Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

設定值，如同 XML 檔案的 XPath 查詢所指定。  
  
## 參數  
 下表說明 `XmlPoke` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Namespaces`|選擇性 `String` 參數。<br /><br /> 指定 XPath 查詢前置詞的命名空間。|  
|`Query`|選擇性 `String` 參數。<br /><br /> 指定 XPath 查詢。|  
|`Value`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定輸出檔。|  
|`XmlInputPath`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定為檔案路徑形式的 XML 輸入。|  
  
## 備註  
 除了會有表中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)