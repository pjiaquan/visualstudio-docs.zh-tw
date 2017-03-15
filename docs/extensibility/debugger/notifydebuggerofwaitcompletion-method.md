---
title: "NotifyDebuggerOfWaitCompletion 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NotifyDebuggerOfWaitCompletion 方法中，工作類別 [.NET Framework 偵錯引擎]"
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# NotifyDebuggerOfWaitCompletion 方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

預留位置方法作為偵錯工具的中斷點目標。 這個方法不能內嵌或最佳化。  
  
 **命名空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件:** mscorlib \(在 mscorlib.dll\)  
  
## 語法  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## 備註  
 如果其偵錯工具通知位元會設定所有的聯結作業，與工作應該呼叫這個方法。  
  
## 需求  
  
## 請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)