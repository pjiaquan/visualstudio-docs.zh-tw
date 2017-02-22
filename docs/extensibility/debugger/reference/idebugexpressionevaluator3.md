---
title: "IDebugExpressionEvaluator3 | Microsoft Docs"
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
  - "IDebugExpressionEvaluator3 介面"
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 增強的剖析樹狀結構表示的運算式評估工具 \(EE\)。  
  
## 語法  
  
```  
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2  
```  
  
## 呼叫端資訊  
 這個版本的剖析器傳遞的符號提供者和鑑定框架的位址。  
  
## 方法  
 除了在方法 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) 介面，這個介面會實作下列方法︰  
  
|方法|描述|  
|--------|--------|  
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|將運算式字串轉換成剖析的運算式，在指定的符號提供者和鑑定框架的位址。|  
  
## 需求  
 標頭︰ Ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll