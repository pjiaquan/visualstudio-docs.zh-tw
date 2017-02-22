---
title: "IDebugStackFrame3 | Microsoft Docs"
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
  - "IDebugStackFrame3"
helpviewer_keywords: 
  - "IDebugStackFrame3 介面"
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會擴充[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)處理被攔截的例外狀況。  
  
## 語法  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 實作的同一個物件上實作這個介面[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面以支援被攔截的例外狀況。  
  
## 呼叫者的備忘稿  
 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugStackFrame2`以取得這個介面的介面。  
  
## 方法 Vtable 順序  
 除了從繼承的方法[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)， `IDebugStackFrame3`會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|處理目前的堆疊框架之前任何規則的例外處理的例外狀況。|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|如果發生堆疊回溯，則傳回程式碼內容。|  
  
## 備註  
 被攔截的例外狀況表示偵錯工具在任何標準的例外處理常式呼叫的執行階段之前，可以處理例外狀況。  本質上攔截例外狀況，表示將假裝就算沒有例外處理常式的執行的時間。  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)\(唯一的例外是如果您正在偵錯混合模式的程式碼 \(managed 和 unmanaged 程式碼\)，在這種情況不會攔截例外狀況在最後一次機會回呼時\) 的所有標準的例外狀況回呼事件時會呼叫。  如果未實作 DE `IDebugStackFrame3`，或 DE 傳回錯誤 IDebugStackFrame3::`InterceptCurrentException` \(例如`E_NOTIMPL`\)，然後偵錯工具處理例外狀況的一般。  
  
 藉由攔截例外狀況，偵錯工具可以讓使用者對程式進行偵錯的狀態的變更，然後繼續執行，在擲回例外狀況的位置。  
  
> [!NOTE]
>  被攔截的例外狀況只被允許在受管理的程式碼，也就是在通用語言執行階段 \(CLR\) 下執行的程式。  
  
 偵錯引擎指出它支援攔截的例外狀況，藉由設定"metricExceptions"設為 1 的值在執行階段使用`SetMetric`函式。  如需詳細資訊，請參閱 [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)