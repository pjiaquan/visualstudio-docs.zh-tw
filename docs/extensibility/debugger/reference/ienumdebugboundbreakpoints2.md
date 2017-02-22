---
title: "IEnumDebugBoundBreakpoints2 | Microsoft Docs"
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
  - "IEnumDebugBoundBreakpoints2"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2"
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugBoundBreakpoints2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會列舉繫結相關聯的暫止中斷點的中斷點或中斷點繫結事件。  
  
## 語法  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面支援中斷點的一部分。  如果支援中斷點，就必須實作這個介面。  
  
## 呼叫者的備忘稿  
 Visual Studio 的呼叫：  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)若要取得這個介面表示一份已觸發的所有中斷點。  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)若要取得這個介面表示一份已繫結的所有中斷點。  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)若要取得這個介面表示一份所有繫結至該暫止中斷點的中斷點。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugBoundBreakpoints2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|擷取指定的列舉型別序列中的繫結中斷點。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|略過指定的數目的列舉型別序列中的繫結中斷點。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|取得列舉值中的繫結中斷點的數目。|  
  
## 備註  
 Visual Studio 會使用這個介面表示繫結的中斷點，以更新顯示在 IDE 中的中斷點。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)