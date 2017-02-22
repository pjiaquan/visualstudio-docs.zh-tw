---
title: "IDebugCustomAttribute | Microsoft Docs"
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
  - "IDebugCustomAttribute"
helpviewer_keywords: 
  - "IDebugCustomAttribute 介面"
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示自訂屬性，而且它可以提供名稱、 父節點和屬性的類別型別。  
  
## 語法  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## 實作器注意事項  
 符號提供者會實作這個介面以支援與符號相關的自訂屬性。  它通常是在其本身的物件上實作。  
  
## 呼叫者的備忘稿  
 呼叫[下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)會傳回這個介面。  呼叫[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)方法傳回[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugCustomAttribute`。  
  
|方法|描述|  
|--------|--------|  
|[GetParentField](../Topic/IDebugCustomAttribute::GetParentField.md)|取得目前屬性所連接的欄位。|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|取得自訂屬性類別的型別。|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|取得自訂屬性的名稱。|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|取得屬性資訊，以位元組為單位的 blob。|  
  
## 備註  
 自訂屬性是 C\#，提供特定的類別或方法相關聯的自訂中繼資料的結構。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)