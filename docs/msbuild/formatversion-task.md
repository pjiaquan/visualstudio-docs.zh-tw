---
title: "FormatVersion Task | Microsoft Docs"
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
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FormatVersion Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將修訂編號附加至版本號碼。  
  
-   案例 \#1：輸入：Version\=\<undefined\>;  Revision\=\<don't care\>;   輸出：OutputVersion\="1.0.0.0"  
  
-   案例 \#2：輸入：Version\="1.0.0.\*"  Revision\="5"  輸出：OutputVersion\="1.0.0.5"  
  
-   案例 \#3：輸入：Version\="1.0.0.0"  Revision\=\<don't care\>;  輸出：OutputVersion\="1.0.0.0"  
  
## 參數  
 下表說明 `FormatVersion` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`FormatType`|選擇性 `String` 參數。<br /><br /> 指定格式類型。<br /><br /> -   "Version" \= 版本。<br />-   "Path" \= 以 "\_" 取代 "."；|  
|`OutputVersion`|選擇性 `String` 輸出參數。<br /><br /> 指定包含修訂編號的輸出版本。|  
|`Revision`|選擇性 `Int32` 參數。<br /><br /> 指定要附加至版本的修訂。|  
|`Version`|選擇性 `String` 參數。<br /><br /> 指定要格式化的版本號碼字串。|  
  
## 備註  
 除了會有表中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)