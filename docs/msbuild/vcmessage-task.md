---
title: "VCMessage Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.vcmessage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "VCMessage task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), VCMessage task"
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# VCMessage Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

記錄建置期間的警告和錯誤訊息。  
  
## 備註  
 這項工作可協助實作 MSBuild for Visual C\+\+，並不適合由使用者呼叫。  如需詳細資訊，請參閱 <xref:Microsoft.Build.Utilities.TaskLoggingHelper>。  
  
## 參數  
 下表描述 **VCMessage**  工作的參數。  
  
|參數|描述|  
|--------|--------|  
|**Arguments**|選擇性 **String** 參數。<br /><br /> 要顯示之訊息的清單，以分號分隔。|  
|**Code**|必要的 **String** 參數。<br /><br /> 限定訊息的錯誤號碼。|  
|**Type**|選擇性 **String** 參數。<br /><br /> 指定要發出之訊息的類型。  指定 `"Warning"` 發出警告訊息，或指定 `"Error"` 發出錯誤訊息。|  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)