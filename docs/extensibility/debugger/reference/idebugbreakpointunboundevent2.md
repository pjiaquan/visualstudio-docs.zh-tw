---
title: "IDebugBreakpointUnboundEvent2 | Microsoft Docs"
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
  - "IDebugBreakpointUnboundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2"
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointUnboundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會告知偵錯叢集 \(SDM\) 繫結的中斷點已被解除載入的程式與繫結。  
  
## 語法  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面支援中斷點的一部分。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件 \(使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面\)。  
  
## 呼叫者的備忘稿  
 DE 建立並繫結的中斷點未繫結時，會傳送這個事件的物件。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，由 SDM 提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugBreakpointUnboundEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|取得成為未繫結中斷點。|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|取得中斷點是未繫結的原因。|  
  
## 備註  
 當偵錯引擎 DLL 或類別卸載時，繫結到該模組中的程式碼的所有中斷點都必須解除繫結正在進行偵錯的程式。  `IDebugBreakpointUnboundEvent2`傳送時每一個未繫結的中斷點。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)