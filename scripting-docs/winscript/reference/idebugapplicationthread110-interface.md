---
title: "IDebugApplicationThread110 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110 介面"
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThread110 介面
提供 [IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md) 介面提供的功能。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 方法  
 `IDebugApplicationThread110` 介面公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|在主執行緒進行非同步呼叫。|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|的設計是要執行緒從 PDM 的執行緒切換機制的要求目前的處理序。  通常是 0 或 1，不過，它有可能有可以更高，如果處理一執行緒呼叫的開頭，但是觸發同步呼叫執行緒或暫止執行緒 \(例如，藉由觸發程序會在偵錯工具執行緒上執行的 IDebugApplicationEvents 事件|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) 上的這個執行緒和尚未完成。|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|這個執行緒可以處理 PDM 的執行緒切換機制進行的呼叫的狀態 \(例如 SynchronousCallInThread\)。|