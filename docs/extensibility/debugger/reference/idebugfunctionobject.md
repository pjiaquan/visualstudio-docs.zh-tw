---
title: "IDebugFunctionObject | Microsoft Docs"
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
  - "IDebugFunctionObject"
helpviewer_keywords: 
  - "IDebugFunctionObject 介面"
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面表示函式。  
  
## 語法  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## 實作者注意事項  
 運算式評估工具會實作這個介面來表示函式。  
  
## 呼叫端資訊  
 這個介面是特製化的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面，並使用取得 [QueryInterface](/visual-cpp/atl/queryinterface) 上 `IDebugObject` 介面。  
  
## 依照 Vtable 順序的方法  
 除了繼承自方法 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), 、 `IDebugFunctionObject` 介面會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|建立基本資料物件。|  
|[建立物件](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|建立使用建構函式的物件。|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|沒有建構函式建立物件。|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|建立陣列物件。|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|建立字串物件。|  
|[評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|呼叫函式，並傳回產生的值做為物件。|  
  
## 備註  
 這個介面可讓運算式評估工具，來代表剖析樹狀結構中的函式。`Create` 中此介面的方法用來建構物件，代表輸入的參數的方法。 函式，就可以執行呼叫 [評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 方法，傳回物件，表示函式的傳回值。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)