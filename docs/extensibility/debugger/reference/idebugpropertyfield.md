---
title: "IDebugPropertyField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyField"
helpviewer_keywords: 
  - "IDebugPropertyField 介面"
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPropertyField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會提供允許取得和設定屬性的函式。  
  
## 語法  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## 實作器注意事項  
 符號提供者實作的同一個物件上實作這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)。  這個介面會是特製化類別支援屬性的概念。  
  
## 呼叫者的備忘稿  
 使用[QueryInterface](/visual-cpp/atl/queryinterface)以取得這個介面，從[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面如果[GetKind](../Topic/IDebugField::GetKind.md)方法傳回`FIELD_KIND_PROP`。  
  
## 方法 Vtable 順序  
 除了在方法[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)和[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|取得取得屬性的方法。|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|取得設定屬性的方法。|  
  
## 備註  
 屬性是 managed 程式碼的概念，因此表示會被視為變數的方法。  屬性不受管理的 c \+ \+ 中不是存在。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)