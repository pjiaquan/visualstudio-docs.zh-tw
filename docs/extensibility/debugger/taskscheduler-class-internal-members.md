---
title: "TaskScheduler 類別-內部成員 | Microsoft Docs"
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
  - "TaskScheduler 類別 [.NET Framework 偵錯引擎]"
  - "偵錯引擎，TaskScheduler 類別 [.NET Framework]"
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# TaskScheduler 類別-內部成員
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主題描述的內部成員 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 類別可協助您實作自訂的偵錯工具。 如需此類別的一般資訊，請參閱 <xref:System.Threading.Tasks.TaskScheduler> 參考主題。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件︰** mscorlib （在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這些內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## Members  
  
### 方法  
  
|名稱|描述|  
|--------|--------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|擷取所有排定工作的陣列。|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|擷取所有陣列 <xref:System.Threading.Tasks.TaskScheduler> 目前使用中的物件。|  
  
## 備註  
  
## 請參閱  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [.NET Framework 的平行擴充內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)