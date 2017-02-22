---
title: "IEnumDebugFields | Microsoft Docs"
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
  - "IEnumDebugFields"
helpviewer_keywords: 
  - "IEnumDebugFields 介面"
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示實作的物件集合的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。  
  
## 語法  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## 實作器注意事項  
 若要提供實作的物件集的符號提供者會實作這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。  請注意這並非標準的 COM 列舉型別是否受限於[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)方法。  
  
## 呼叫者的備忘稿  
 這個介面會傳回由[GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)和[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)。  
  
## 方法 Vtable 順序  
 這個介面會實作下列方法。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|擷取下的一組[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)列舉型別中的物件。|  
|[Skip](../Topic/IEnumDebugFields::Skip.md)|略過指定的數目的項目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|將重設第一個項目，為列舉型別。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|擷取一份目前的列舉型別。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|擷取列舉型別中的項目數。|  
  
## 備註  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)