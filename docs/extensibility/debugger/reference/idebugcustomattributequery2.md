---
title: "IDebugCustomAttributeQuery2 | Microsoft Docs"
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
  - "IDebugCustomAttributeQuery2"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery 介面"
  - "IDebugCustomAttributeQuery2 介面"
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

決定此欄位的自訂屬性存在，而且如果它存在時，傳回屬性資訊。  
  
## 語法  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## 實作器注意事項  
 符號提供者實作的同一個物件上實作這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)以支援自訂屬性。  
  
## 呼叫者的備忘稿  
 使用[QueryInterface](/visual-cpp/atl/queryinterface)以取得這個介面，從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法 **IDebugCustomAttributeQuery** 介面。  
  
|方法|描述|  
|--------|--------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|判斷自訂屬性是否存在的名稱。|  
|[GetCustomAttributeByName](../Topic/IDebugCustomAttributeQuery2::GetCustomAttributeByName.md)|取得指定的自訂屬性的屬性資訊。|  
  
 除了 **IDebugCustomAttributeQuery** 方法， `IDebugCustomAttributeQuery2`實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|取得附加至這個欄位的所有自訂屬性的列舉值。|  
  
## 備註  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)方法會傳回為這個欄位定義的所有自訂屬性的列舉值。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)