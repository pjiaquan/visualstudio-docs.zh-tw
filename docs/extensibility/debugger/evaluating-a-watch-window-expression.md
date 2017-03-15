---
title: "監看式] 視窗中的運算式評估 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "監看式] 視窗中的運算式"
  - "監看式] 視窗中運算式"
  - "運算式評估、 監看式] 視窗中的運算式"
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 監看式] 視窗中的運算式評估
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 當執行暫停時，Visual Studio 會呼叫偵錯引擎 \(DE\) 來判斷其監看清單中的每個運算式的目前值。 DE 評估使用的運算式評估工具 \(EE\)，每個運算式，並顯示其值中的，Visual Studio **監看式** 視窗。  
  
 以下是如何評估監看清單運算式的概觀:  
  
1.  Visual Studio 會呼叫 DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 以取得可用來評估運算式，運算式內容。  
  
2.  監看清單中每一個運算式，Visual Studio 會呼叫 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 將運算式文字轉換成剖析的運算式。  
  
3.  `IDebugExpressionContext2::ParseText` 呼叫 [剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 要剖析的文字和產生的實際工作 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 物件。  
  
4.  `IDebugExpressionContext2::ParseText` 建立 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 物件，並將 `IDebugParsedExpression` 進去的物件。 這個我`DebugExpression2` 物件傳回至 Visual Studio。  
  
5.  Visual Studio 呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 評估已剖析的運算式。  
  
6.  `IDebugExpression2::EvaluateSync` 傳遞至呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 執行實際的評估，並產生 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 會傳回到 Visual Studio 中的物件。  
  
7.  Visual Studio 呼叫 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 取得即會顯示在 \[監看清單的運算式值。  
  
## 剖析，然後評估  
 由於剖析複雜的運算式需要遠比進行評估，運算式的評估程序會分成兩個步驟: 1\) 剖析運算式和 2\) 評估剖析的運算式。 如此一來，評估可能會發生許多次，但必須一次剖析運算式。 中繼剖析的運算式會傳回從中 EE [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 物件，接著封裝並傳回做為 DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 物件。`IDebugExpression` 物件會延後所有評估 `IDebugParsedExpression` 物件。  
  
> [!NOTE]
>  不需要遵守此兩步驟程序，即使 Visual Studio 會假設; EEEE 可以剖析和評估相同的步驟時 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 稱為 \(這是 MyCEE 範例的運作方式，例如\)。 如果您的語言可以構成複雜的運算式，您可能想要剖析步驟分開評估步驟。 許多監看運算式時，這樣會增加效能，在 Visual Studio 偵錯工具會顯示。  
  
## 本章節內容  
 [運算式評估的實作範例](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 您可以使用 MyCEE 範例來逐步完成運算式評估的程序。  
  
 [監看式運算式評估](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 說明成功的運算式剖析之後發生的情況。  
  
## 相關章節  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 提供偵錯引擎 \(DE\) 呼叫運算式評估工具 \(EE\) 時，會傳遞的引數。  
  
## 請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)