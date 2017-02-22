---
title: "運算式評估 | Microsoft Docs"
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
  - "評估運算式 [偵錯 SDK]"
  - "偵錯的 [偵錯 SDK]，運算式評估"
  - "運算式評估"
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 運算式評估
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

運算式被由從 \[自動變數\]、 監看式、 快速監看式或 \[即時運算視窗中傳遞的字串。  評估運算式時，就會產生可列印的字串，包含名稱和型別的變數或引數和它的值。  這個字串會在對應的 IDE 視窗顯示。  
  
## 實作  
 程式已經停止於中斷點時，會評估運算式。  運算式本身由 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面，這表示剖析的運算式可準備進行繫結和評估給定的運算式評估內容中。  堆疊框架會決定偵錯引擎 \(DE\) 提供藉由實作運算式評估內容 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面。  
  
 給予使用者字串和 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面，可以取得偵錯引擎 \(DE\)  [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面，藉由傳遞至使用者字串 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法。  傳回 IDebugExpression2 介面包含剖析準備進行評估的運算式。  
  
 與`IDebugExpression2`介面，DE 可以取得運算式的值同步或非同步運算式的評估，透過使用 [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。  這個值，和名稱和型別的變數或引數，會傳給 IDE 進行顯示。  數值、 名稱和型別由 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面。  
  
 若要啟用運算式評估，就必須實作 DE  [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 和 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面。  同步和非同步的評估會藉由實作的 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法。  
  
## 請參閱  
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)