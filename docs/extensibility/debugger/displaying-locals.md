---
title: "顯示 [區域變數] | Microsoft Docs"
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
  - "運算式評估，顯示 [區域變數]"
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 顯示 [區域變數]
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 永遠執行方法，也就是包含方法或目前方法的內容中進行。 當執行暫停時，Visual Studio 會呼叫的偵錯引擎 \(DE\) 取得一份本機變數和引數，統稱為方法的區域變數。 Visual Studio 會顯示這些區域變數和其值在 **區域變數** 視窗。  
  
 若要顯示 \[區域變數\]，請呼叫 DE [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 屬於 EE 方法，並讓它的評估內容、 符號提供者 \(SP\)、 目前執行位址和繫結器物件。 如需詳細資訊，請參閱[評估內容](../../extensibility/debugger/evaluation-context.md)。 如果呼叫成功， `IDebugExpressionEvaluator::GetMethodProperty` 方法會傳回 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 物件，表示包含目前執行位址的方法。  
  
 DE 呼叫 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 取得 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 物件，這是篩選要傳回唯一的區域變數，以產生一份列舉 [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) 結構。 每個結構會包含名稱、 類型和值的區域變數。 型別和值會儲存為格式化的字串，適合用來顯示。 名稱、 類型和值都會通常顯示在同一行 **區域變數** 視窗。  
  
> [!NOTE]
>  **快速監看式** 和 **監看式** windows 也會顯示變數的名稱、 值和型別相同的格式。 不過，這些值藉由呼叫中取得 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 而不是 `IDebugProperty2::EnumChildren`。  
  
## 在本節中  
 [範例實作的區域變數](../../extensibility/debugger/sample-implementation-of-locals.md)  
 利用範例來逐步實作區域變數的程序。  
  
## 相關章節  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 說明當偵錯引擎 \(DE\) 呼叫運算式評估工具 \(EE\) 時，會傳遞三個引數。  
  
## 請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)