---
title: "IDebugEnumField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField"
helpviewer_keywords: 
  - "IDebugEnumField 介面"
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEnumField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示列舉型別。  
  
## 語法  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## 實作器注意事項  
 符號提供者會實作這個介面表示列舉型別。  
  
## 呼叫者的備忘稿  
 使用[QueryInterface](/visual-cpp/atl/queryinterface)以取得這個介面，從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面如果[GetKind](../Topic/IDebugField::GetKind.md)會傳回`FIELD_TYPE_ENUM`。  
  
## 方法 VTable 順序  
 除了在方法`IDebugField`和`IDebugContainerField`介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述這個列舉型別的名稱。|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|傳回與指定的值相關聯的列舉常數的名稱。|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|傳回指定列舉型別常數名稱相關聯的值|  
|[GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)|傳回具有指定的列舉常數的名稱，但略過的案例相關聯的值。|  
  
## 備註  
 這是基礎實際上會繫結至具有位置的符號[繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)