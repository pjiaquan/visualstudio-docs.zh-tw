---
title: "GetTaskSchedulersForDebugger 方法 | Microsoft Docs"
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
  - "GetTaskSchedulersForDebugger 方法，TaskScheduler 類別 [.NET Framework 偵錯引擎]"
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GetTaskSchedulersForDebugger 方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取所有陣列 <xref:System.Threading.Tasks.TaskScheduler> 目前使用中的物件。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件︰** mscorlib （在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## 傳回值  
 所有陣列 <xref:System.Threading.Tasks.TaskScheduler> 目前作用中的物件 <xref:System.AppDomain>。  
  
## 備註  
 這個方法不具備執行緒安全，不應與其他執行個體同時 <xref:System.Threading.Tasks.TaskScheduler>。 只有當偵錯工具已暫停的其他所有執行緒，應該會呼叫它從偵錯工具。  
  
## 請參閱  
 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)