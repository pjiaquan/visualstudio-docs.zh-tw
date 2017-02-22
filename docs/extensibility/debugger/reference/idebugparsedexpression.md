---
title: "IDebugParsedExpression | Microsoft Docs"
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
  - "IDebugParsedExpression"
helpviewer_keywords: 
  - "IDebugParsedExpression 介面"
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面表示準備要評估的已剖析的運算式。  
  
## 語法  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## 實作者注意事項  
 運算式評估工具會實作這個介面來代表可供評估的已剖析的運算式。  
  
## 呼叫端資訊  
 呼叫 [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 傳回此介面。  
  
## 依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugParsedExpression`。  
  
|方法|描述|  
|--------|--------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|評估已剖析的運算式。|  
  
## 備註  
 當呼叫端是準備要評估的運算式時，它會呼叫 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 傳回 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ，其中包含評估的結果。 評估，然後評估，可讓進行多次評估剖析的運算式剖析、 略過耗時的程序的剖析運算式這兩個部分方法。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)