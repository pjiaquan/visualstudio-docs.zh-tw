---
title: "IDebugBreakpointBoundEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointBoundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointBoundEvent2"
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBreakpointBoundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會告知偵錯叢集 \(SDM\) 暫止中斷點已載入的程式成功地結合。  
  
## 語法  
  
```  
IDebugBreakpointBoundEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面支援中斷點的一部分。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件 \(使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面\)。  
  
## 呼叫者的備忘稿  
 DE 建立，並暫止中斷點來偵錯的程式上成功地繫結時，會傳送這個事件的物件。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，由 SDM 提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugBreakpointBoundEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|取得正在進行繫結的暫止中斷點。|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|建立此事件繫結中斷點的列舉值。|  
  
## 備註  
 只要繫結中斷點，則會將事件傳送至 SDM。  如果中斷點無法繫結， [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)已傳送; 否則， `IDebugBreakpointBoundEvent2`傳送。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)