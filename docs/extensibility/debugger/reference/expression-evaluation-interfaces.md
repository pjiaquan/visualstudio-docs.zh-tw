---
title: "運算式評估介面 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "運算式評估、 介面"
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 運算式評估介面
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 以下是運算式評估介面 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 偵錯 sdk 》。  
  
## 討論  
 這些介面用來評估在中斷模式期間的呼叫堆疊中的運算式。 它們只針對通用語言執行階段運算式評估工具 \(EE\) 進行實作。  
  
 資料表中的每個介面會顯示可以實作下列清單中的元件:  
  
-   偵錯引擎 \(DE\)  
  
-   運算式評估工具 \(EE\)  
  
-   Visual Studio \(VS\)  
  
|介面|實作|描述|  
|--------|--------|--------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|代表變數的數字的別名。|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|代表別名數值變數，並可讓運算式評估工具 \(EE\) 來取得應用程式定義域做為別名。|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|表示陣列物件。|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|表示 managed 的陣列物件，並可讓運算式評估工具 \(EE\) 來判斷陣列的基底的索引 \(下限\)。|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|表示繫結偵錯符號，可在記憶體中的實際位址的繫結器。|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|相同 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 介面但可讓您存取型別、 別名和自訂的視覺化檢視。|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|表示運算式評估工具。|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|表示運算式評估工具 \(EE\) 增強型的版本。|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|增強的剖析樹狀結構表示的運算式評估工具 \(EE\)。|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|表示函式。|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|表示函式，以及增強 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面。|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|可讓偵錯工具的 \[輸出\] 視窗中顯示訊息的運算式評估工具 \(EE\)。|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|代表 managed 程式碼的物件。|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|代表所有符號的基底介面繫結至記憶體位址。|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|相同 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面但有提供其他資訊的存取權。|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|表示剖析準備要評估的運算式。|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|表示的指標。|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|表示剖析樹狀結構中的指標，並擴充 **IDebugPointerObject** 介面。|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|提供修改透過型別視覺化檢視的類型值的能力。|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|提供存取自訂檢視器和類型的視覺化檢視。|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|可建立 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 物件。|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|表示 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件的集合。|  
  
## 請參閱  
 [應用程式開發介面參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [撰寫 CLR 運算式評估工具](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)