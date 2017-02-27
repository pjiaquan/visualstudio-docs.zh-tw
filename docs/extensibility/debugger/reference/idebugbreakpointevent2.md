---
title: "IDebugBreakpointEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointEvent2 介面"
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

偵錯引擎 \(DE\) 可將這個介面傳送到工作階段偵錯管理員 \(SDM\)，而當程式停止於中斷點時。  
  
## 語法  
  
```  
IDebugBreakpointEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面支援中斷點的一部分。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件 \(使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面\)。  
  
## 呼叫者的備忘稿  
 DE 建立，並在程式中遇到一個以上的中斷點時，會傳送這個事件的物件。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，由 SDM 提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugBreakpointEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|建立在目前的程式碼位置所引發的所有中斷點的列舉值。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)