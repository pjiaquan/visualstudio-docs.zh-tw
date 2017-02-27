---
title: "IDebugEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2"
helpviewer_keywords: 
  - "IDebugEvent2 介面"
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面用來傳達重要的偵錯資訊，例如停止於中斷點，，以及非關鍵的資訊，例如偵錯訊息。  
  
## 語法  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 和自訂的連接埠提供者上實作這個介面與其他所有的事件介面相同的物件。  
  
## 呼叫者的備忘稿  
 使用介面識別碼 \(IID\) 引數提供給[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)或[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)，工作階段偵錯管理員 \(SDM\) 會呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugEvent2`以取得適當的事件介面的介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|取得此偵錯事件的屬性。|  
  
## 備註  
 更明確的事件介面，例如[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)，並不是衍生自 IDebugEvent2 介面，但改實作為個別的介面上相同的物件，做為`IDebugEvent2`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)