---
title: "IDebugExpression2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2"
helpviewer_keywords: 
  - "IDebugExpression2 介面"
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugExpression2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示剖析的運算式可供繫結和評估。  
  
## 語法  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面表示剖析的運算式即可進行評估。  
  
## 呼叫者的備忘稿  
 呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)會傳回這個介面。  [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)傳回[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。  這些介面在偵錯程式已暫停，而且堆疊框架使用時，才可以存取。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugExpression2`。  
  
|方法|描述|  
|--------|--------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步方式評估此運算式。|  
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步運算式的評估。|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式評估此運算式。|  
  
## 備註  
 程式已停止執行，當工作階段偵錯管理員 \(SDM\) 會從呼叫 DE 取得堆疊框架[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。  SDM 會呼叫[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)以取得[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。  這後面會呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)來建立`IDebugExpression2`介面，這表示剖析準備好要評估的運算式。  
  
 SDM 會呼叫其中一個[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)實際上評估運算式，並產生一個值。  
  
 在實作中的`IDebugExpressionContext2::ParseText`，DE 使用 COM 的`CoCreateInstance`函式來具現化的運算式評估工具，並取得[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)介面 \(請參閱範例`IDebugExpressionEvaluator`介面\)。  接著再呼叫 DE [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)以取得[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)介面。  此介面用在實作中的`IDebugExpression2::EvaluateSync`和`IDebugExpression2::EvaluateAsync`以執行評估。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)