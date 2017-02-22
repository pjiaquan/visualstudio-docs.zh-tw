---
title: "實作運算式評估工具 | Microsoft Docs"
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
  - "運算試評估工具"
  - "偵錯的 [偵錯 SDK]，運算式評估工具"
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 實作運算式評估工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 評估運算式是偵錯引擎 \(DE\)、 符號提供者 \(SP\)、 繫結器物件與運算式評估工具 \(EE\) 本身之間的錯綜複雜。 四個元件會透過介面實作的一個元件，並由另一個連接。  
  
 EE 採用運算式從字串的形式 DE 和剖析或會評估它。 EE 實作是由下列介面︰  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 EE 呼叫繫結器物件，提供的是，若要取得的符號和物件的值。 EE 使用下列介面，這些 DE 所實作的介面︰  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 EE 實作 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)。`IDebugProperty2` 提供機制讓您描述運算式評估，例如本機變數、 基本型別或物件，Visual studio，然後顯示中的相關資訊的結果 **區域變數**, ，**監看式**, ，或 **即時運算** 視窗。  
  
 預存程序 EE 由 DE 時指定它要求資訊。 預存程序會實作介面描述位址欄位，例如下列介面和其衍生項目︰  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 EE 會消耗所有這些介面。  
  
## 在本節中  
 [運算式評估工具的實作策略](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 定義三個步驟程序，運算式評估工具 \(EE\) 實作策略。  
  
## 請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)