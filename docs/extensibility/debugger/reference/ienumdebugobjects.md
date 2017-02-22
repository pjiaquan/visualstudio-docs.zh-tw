---
title: "IEnumDebugObjects | Microsoft Docs"
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
  - "IEnumDebugObjects"
helpviewer_keywords: 
  - "IEnumDebugObjects 介面"
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面表示物件的集合實作 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面。  
  
## 語法  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## 實作者注意事項  
 運算式評估工具會實作這個介面可提供實作的物件集的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面。 請注意，這不是標準的 COM 列舉的緣故 [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) 方法。  
  
## 呼叫端資訊  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) 傳回這個介面。  
  
## 依照 Vtable 順序的方法  
 這個介面會實作下列方法。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|擷取下的一組 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 列舉中的物件。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|略過指定的數目的項目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|將列舉型別重設為第一個項目。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|擷取一份目前的列舉。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|擷取列舉中的項目數。|  
  
## 備註  
 這個介面可讓偵錯引擎來列舉一組的陣列中的物件。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)