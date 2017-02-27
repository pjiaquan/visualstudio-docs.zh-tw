---
title: "GetScheduledTasksForDebugger 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetScheduledTasksForDebugger 方法，TaskScheduler 類別 [.NET Framework 偵錯引擎]"
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GetScheduledTasksForDebugger 方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取所有排定工作的陣列。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件︰** mscorlib （在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## 傳回值  
 所有排程工作的陣列。 每個工作正在執行，或已完成執行。  
  
## 備註  
 這個方法不具備執行緒安全，不應與其他執行個體同時 <xref:System.Threading.Tasks.TaskScheduler> 它時，應該呼叫從偵錯工具只偵錯工具已暫停的其他所有執行緒。  
  
## 請參閱  
 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)