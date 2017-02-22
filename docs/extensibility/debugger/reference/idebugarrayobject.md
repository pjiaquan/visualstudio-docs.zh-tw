---
title: "IDebugArrayObject | Microsoft Docs"
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
  - "IDebugArrayObject"
helpviewer_keywords: 
  - "IDebugArrayObject 方法"
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會表示陣列物件。  
  
## 語法  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## 實作者注意事項  
 運算式評估工具會實作此介面，以代表陣列。  
  
## 呼叫端資訊  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面可以取得此介面使用 [QueryInterface](/visual-cpp/atl/queryinterface) 如果表示的物件陣列。  
  
## 依照 Vtable 順序的方法  
 除了在方法 `IDebugObject` 介面上實作下列方法 `IDebugArrayObject` 介面。  
  
|方法|描述|  
|--------|--------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|取得陣列中的項目計數。|  
|[GetElement](../Topic/IDebugArrayObject::GetElement.md)|取得陣列的項目。|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|取得陣列的所有項目。|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|取得陣列的陣序規範。|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|取得陣列維度。|  
  
## 備註  
 運算式評估工具會使用這個介面，代表剖析樹狀結構中的陣列。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)