---
title: "IDebugBreakpointRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2 介面"
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示建立與繫結任何中斷點類型的必要資訊。  
  
## 語法  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## 實作器注意事項  
 工作階段偵錯管理員 \(SDM\) 通常會實作這個介面。  
  
## 呼叫者的備忘稿  
 偵錯引擎 \(DE\) 接收到這個介面，透過呼叫[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) ，以建立暫止中斷點。  呼叫[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)可從 DE 擷取這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugBreakpointRequest2`。  
  
|方法|描述|  
|--------|--------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|取得此中斷點要求的中斷點位置類型。|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|取得描述這個中斷點要求中斷點要求資訊。|  
  
## 備註  
 之後的程式進行偵錯載入器之後，呼叫[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)會暫止中斷點繫結到要求的程式中的位置。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)