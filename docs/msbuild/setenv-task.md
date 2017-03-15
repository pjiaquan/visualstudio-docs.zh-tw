---
title: "SetEnv Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.setenv"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tasks"
  - "SetEnv task (MSBuild (Visual C++))"
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# SetEnv Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

設定或刪除指定之環境變數的值。  
  
## 參數  
 下表描述 **SetEnv**  工作的參數。  
  
|參數|描述|  
|--------|--------|  
|**Name**|必要的 **String** 參數。<br /><br /> 環境變數的名稱。|  
|**OutputEnvironmentVariable**|選擇性 **String** 輸出參數。<br /><br /> 包含指派給 **Name** 參數所指定之環境變數的值。|  
|**Prefix**|強制的 `Boolean` 參數。<br /><br /> 如果 `true` 串連 **Name** 參數指定之環境變數之前的 **Value** 參數，則將結果指派給環境變數。  如果 `false`，只會將 **Value** 參數的值指派給環境變數。|  
|**Target**|選擇性 **String** 參數。<br /><br /> 指定儲存環境變數的位置。  指定 "`User`" 或 "`Machine`"。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上的 "EnvironmentVariableTarget 列舉"。|  
|**Value**|選擇性 **String** 參數。<br /><br /> 指派給 **Name** 參數所指定之環境變數的值。  如果 **Value** 是空的而且有變數存在，則會刪除變數。  如果變數不存在，即使無法執行作業，也不會發生任何錯誤。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上的 "Environment::SetEnvironmentVariable 方法"。|  
  
## 備註  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)