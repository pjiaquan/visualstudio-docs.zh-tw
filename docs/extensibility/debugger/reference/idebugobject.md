---
title: "IDebugObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject"
helpviewer_keywords: 
  - "IDebugObject 介面"
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面表示繫結器會將封裝的符號和運算式的值的物件。  
  
## 語法  
  
```  
IDebugObject : IUnknown  
```  
  
## 實作者注意事項  
 運算式評估工具會實作這個介面來表示的物件。  
  
## 呼叫端資訊  
 這個介面是運算式評估工具會使用已剖析的運算式中的所有物件的基底類別。 它由呼叫 [繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md) 方法。[QueryInterface](/visual-cpp/atl/queryinterface) 從這個介面取得更具特製化的介面。  
  
## 依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugObject`。  
  
|方法|描述|  
|--------|--------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|取得物件的大小。|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|取得物件的值做為一系列連續的位元組。|  
|[Setvalue 巨集](../Topic/IDebugObject::SetValue.md)|設定物件的值從一系列連續的位元組。|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|設定此物件的參考值。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|取得代表值的物件位址的記憶體內容。|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|偵錯引擎的位址空間中建立受管理物件的複本。|  
|[IsNullReference](../Topic/IDebugObject::IsNullReference.md)|測試是否此物件為 null 參考。|  
|[IsEqual](../Topic/IDebugObject::IsEqual.md)|比較這個物件。|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|判斷此物件是否為唯讀。|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|判斷物件是否為透明的 proxy。|  
  
## 備註  
 運算式評估工具會使用此介面的基底類別來表示剖析樹狀結構中的物件。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../Topic/IDebugArrayObject::GetElement.md)   
 [繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)