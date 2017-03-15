---
title: "索引鍵運算式評估工具介面 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯的 [偵錯 SDK]，運算式評估"
  - "運算式評估、 介面"
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 索引鍵運算式評估工具介面
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 在撰寫運算式評估工具 \(EE\)，以及評估內容時，您應該熟悉下列介面。  
  
## 介面描述  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     具有單一方法， [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), ，此 cmdlet 會取得資料結構，代表目前執行點。 此資料結構是一個三個引數的偵錯引擎 \(DE\) 傳遞給 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 方法來評估運算式。 符號提供者通常實作這個介面。  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     具有 [繫結](../../extensibility/debugger/reference/idebugbinder-bind.md) 方法，取得包含目前的符號值的記憶體區域。 指定這兩個包含方法，由 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 物件，以及符號本身，由 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 物件， `IDebugBinder::Bind` 傳回符號的值。`IDebugBinder` 通常是由 DE 實作。  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     表示簡單資料型別。 對於更複雜的型別，例如陣列和方法，使用衍生 [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) 和 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 分別介面。[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 這另一個重要的衍生的介面符號表示包含其他符號，例如方法或類別。`IDebugField` 符號提供者通常實作介面 （和其衍生項目）。  
  
     `IDebugField` 物件可以用來尋找名稱和類型的符號，搭配 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 物件，可以用來尋找其值。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     代表實際的位元執行階段值的符號。[繫結](../../extensibility/debugger/reference/idebugbinder-bind.md) 採用 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 物件，代表符號，並且傳回 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 物件。[GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) 方法會傳回符號的值在記憶體緩衝區。 DE 通常會實作這個介面來代表記憶體中的屬性值。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     這個介面表示運算式評估工具本身。 重要的方法是 [剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), ，它會傳回 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 介面。  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     這個介面表示準備要評估的已剖析的運算式。 重要的方法是 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) IDebugProperty2 會傳回代表的值和運算式的類型。  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     此介面表示值和其型別，而且是運算式評估的結果。  
  
## 請參閱  
 [評估內容](../../extensibility/debugger/evaluation-context.md)