---
title: "當中斷點繫結，或會變成未繫結 | Microsoft Docs"
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
  - "偵錯 [偵錯 SDK] 時，中斷點未繫結的事件"
  - "中斷點繫結事件"
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 當中斷點繫結，或會變成未繫結
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當中斷點無法繫結時，呼叫後，  [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) 方法、 繫結時間，並建立這個中斷點的時間不同。  
  
## 呼叫的方法  
 工作階段偵錯管理員 \(SDM\) 會呼叫下列方法：  
  
1.  [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)。  DE 傳回 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)。  
  
2.  [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)。  
  
3.  [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)。  
  
4.  [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 方法，並傳回 S\_OK。  DE 傳送 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 或 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)。  
  
5.  [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 和 [IDebugBreakpointBoundEvent2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 方法以驗證並取得繫結的中斷點。  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)