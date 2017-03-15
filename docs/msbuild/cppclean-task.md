---
title: "CPPClean Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.cppclean"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), CPPClean task"
  - "CPPClean task (MSBuild (Visual C++))"
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# CPPClean Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

刪除 MSBuild 在建置 Visual C\+\+ 專案時建立的暫存檔案。  刪除建置檔的處理序稱為「*清理*」\(Cleaning\)。  
  
## 參數  
 下表描述 **CPPClean**  工作的參數。  
  
|參數|描述|  
|--------|--------|  
|**DeletedFiles**|選擇性 `ITaskItem[]` 輸出參數。<br /><br /> 定義可由工作使用和發出的 MSBuild 輸出檔項目陣列。|  
|**DoDelete**|選擇性 **Boolean** 參數。<br /><br /> 如果 `true`，請清除暫存的建置檔。|  
|**FilePatternsToDeleteOnClean**|必要的 `String` 參數。<br /><br /> 指定要清理之副檔名的清單，以分號分隔。|  
|**FilesExcludedFromClean**|選擇性 `String` 參數。<br /><br /> 指定不要清理之檔案的清單，以分號分隔。|  
|**FoldersToClean**|必要的 `String` 參數。<br /><br /> 指定要清理之目錄的清單，以分號分隔。  您可以指定完整或相對路徑，此路徑可以包含萬用字元符號 \(**\***\)。|  
  
## 備註  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)