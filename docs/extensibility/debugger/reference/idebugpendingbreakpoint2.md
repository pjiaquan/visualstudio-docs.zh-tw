---
title: "IDebugPendingBreakpoint2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2 介面"
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示已準備好要繫結至程式碼位置的中斷點。  
  
## 語法  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面支援中斷點的一部分。  
  
## 呼叫者的備忘稿  
 呼叫[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)建立的暫止中斷點，從[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面。  呼叫[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)會建立`IDebugBreakpoint2` ，表示繫結的中斷點在程式中的介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugPendingBreakpoint2`。  
  
|方法|描述|  
|--------|--------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|決定是否暫止中斷點可以繫結至程式碼的位置。|  
|[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|將暫止中斷點繫結至一或多個程式碼的位置。|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|取得這個暫止中斷點的狀態。|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|取得用來建立這個暫止中斷點的中斷點要求。|  
|[虛擬化](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|切換虛擬化的狀態的暫止中斷點。|  
|[啟用](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換這暫止中斷點的啟用的狀態。|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|設定或變更相關聯這暫止中斷點的條件。|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|設定或變更擱置中的中斷點耗費通過計數。|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|列舉所有繫結從暫止中斷點的中斷點。|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|列舉，導因於此的暫止中斷點的所有錯誤中斷點。|  
|[刪除](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除此暫止中斷點，並從其繫結的所有中斷點。|  
  
## 備註  
 `IDebugPendingBreakpoint2`可以視為繫結中斷點，可套用至一或多個程式的程式碼所需的所有必要資訊的提供者。  
  
 暫止中斷點可能會產生一個以上的繫結的中斷點。  例如，c \+ \+ 樣式範本中的中斷點可能會產生每個唯一的執行個體，該範本的繫結的中斷點。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)