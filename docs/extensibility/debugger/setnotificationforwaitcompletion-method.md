---
title: "SetNotificationForWaitCompletion 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SetNotificationForWaitCompletion 方法中，工作類別 [.NET Framework 偵錯引擎]"
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# SetNotificationForWaitCompletion 方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

設定或清除 TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION 狀態位元。  
  
 **命名空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件:** mscorlib \(在 mscorlib.dll\)  
  
## 語法  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### 參數  
 `enabled`  
  
 `true` 設定位元。 `false` 未設定為位元。  
  
## 例外狀況  
  
## 備註  
 偵錯工具設定此位元協助跳離非同步方法的主體。 如果 `enabled` 是 `true`, ，必須只能在尚未完成的工作上呼叫這個方法。 如果 `enabled` 是 `false`, ，這個方法可呼叫已完成的工作上。 在可能情況下，它應該只用於承諾樣式工作。  
  
## 需求  
  
## 請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)