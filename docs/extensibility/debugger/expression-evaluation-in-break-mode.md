---
title: "在中斷模式中的運算式評估 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中斷模式中，運算式評估"
  - "偵錯的 [偵錯 SDK]，運算式評估"
  - "運算式評估、 中斷模式"
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 在中斷模式中的運算式評估
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下列說明程序的偵錯工具處於中斷模式，且必須進行運算式評估時發生。  
  
## 運算式評估程序  
 這些是評估運算式所需的基本步驟：  
  
1.  工作階段偵錯管理員 \(SDM\) 會呼叫 [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 以取得運算式內容介面， [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)。  
  
2.  SDM 會呼叫 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 與要剖析的字串。  
  
3.  如果 ParseText 不會傳回 S\_OK，則會傳回錯誤的原因。  
  
     \-否則\-  
  
     如果 ParseText 並不會傳回 S\_OK，SDM 就可以呼叫其中一個 [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 取得剖析的運算式的最後一個值。  
  
    -   如果是使用`IDebugExpression2::EvaluateSync`，指定的回呼介面用來傳達評估的持續的程序。  最終的值會傳回在 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面。  
  
    -   如果是使用`IDebugExpression2::EvaluateAsync`，指定的回呼介面用來傳達評估的持續的程序。  評估完成後，會傳送 EvaluateAsync  [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 透過回呼介面。  使用這個事件的介面，可取得的最後一個值與[GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)。  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)