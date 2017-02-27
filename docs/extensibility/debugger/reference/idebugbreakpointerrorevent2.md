---
title: "IDebugBreakpointErrorEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointErrorEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointErrorEvent2"
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointErrorEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會告知偵錯叢集 \(SDM\) 暫止中斷點可能沒有結合到載入的程式，可能導因於警告或錯誤。  
  
## 語法  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面支援中斷點的一部分。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件 \(使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面\)。  
  
## 呼叫者的備忘稿  
 DE 建立，並暫止中斷點無法繫結至偵錯程式時，會傳送這個事件的物件。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，由 SDM 提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugBreakpointErrorEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|取得[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) ，描述的警告或錯誤的介面。|  
  
## 備註  
 只要繫結中斷點，則會將事件傳送至 SDM。  如果中斷點無法繫結， `IDebugBreakpointErrorEvent2`已傳送; 否則， [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)傳送。  
  
 比方說，當相關聯的暫止中斷點的條件，就無法剖析或評估，警告訊息會傳送無法將暫止中斷點繫結，這一次。  這可能是因為尚未尚未載入中斷點的程式碼。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)