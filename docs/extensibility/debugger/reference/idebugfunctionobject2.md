---
title: "IDebugFunctionObject2 | Microsoft Docs"
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
  - "IDebugFunctionObject2 介面"
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示函式，以及增強 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面。  
  
## 語法  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## 實作者注意事項  
 運算式評估工具 \(EE\) 會實作這個介面來表示函式。  
  
## 呼叫端資訊  
 這個介面的方法會延後的 **IDebugFunctionObject** 如下︰  
  
-   **IDebugEvaluate** 方法會採用旗標。  
  
-   **CreateObject** 方法會採用旗標和逾時。  
  
-   **CreateStringObjectWithLength** 方法會採用的長度。  
  
## 方法  
 這個介面會實作下列方法︰  
  
|方法|描述|  
|--------|--------|  
|[建立物件](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|建立會使用指定評估旗標設定和逾時值的建構函式的物件。|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|建立具有指定的長度的字串物件。|  
|[評估](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|呼叫函式，並傳回產生的值做為物件。|  
  
## 需求  
 標頭︰ Ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll