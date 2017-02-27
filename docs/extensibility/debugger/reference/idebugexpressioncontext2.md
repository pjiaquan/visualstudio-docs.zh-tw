---
title: "IDebugExpressionContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionContext2"
helpviewer_keywords: 
  - "IDebugExpressionContext2 介面"
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示運算式評估內容  
  
## 語法  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面表示可以被評估運算式的內容。  
  
## 呼叫者的備忘稿  
 呼叫[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)會傳回這個介面。  已暫停正在進行偵錯的程式，而且一個堆疊框架是可用，這個介面是可存取。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugExpressionContext2`。  
  
|方法|描述|  
|--------|--------|  
|[GetName](../Topic/IDebugExpressionContext2::GetName.md)|擷取評估內容的名稱。|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|剖析文字為主的運算式評估。|  
  
## 備註  
 評估內容可以視為執行運算式評估的範圍。  
  
 程式已停止執行，當工作階段偵錯管理員 \(SDM\) 會從呼叫 DE 取得堆疊框架[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。  SDM 會呼叫[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)以取得`IDebugExpressionContext2`介面。  這後面會呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)來建立[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)介面，這表示剖析準備好要評估的運算式。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)