---
title: "IDebugErrorBreakpoint2 | Microsoft Docs"
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
  - "IDebugErrorBreakpoint2"
helpviewer_keywords: 
  - "IDebugErrorBreakpoint2 介面"
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugErrorBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示錯誤或警告中斷點，例如無效的位置、 無效的運算式或為什麼暫止中斷點擁有未繫結 \(程式碼不會載入尚未等等\) 的原因。  
  
## 語法  
  
```  
IDebugErrorBreakpoint2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎會實作這個介面支援中斷點的一部分。  這個介面用來報告問題，以及繫結中斷點。  
  
## 呼叫者的備忘稿  
 呼叫[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)會取得這個介面。  此介面也可能會傳回 \(部分清單，以表示為[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)介面\) 呼叫[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)或[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugErrorBreakpoint2`。  
  
|方法|描述|  
|--------|--------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|取得造成錯誤的暫止中斷點。|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|取得描述錯誤的中斷點錯誤解析度。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)