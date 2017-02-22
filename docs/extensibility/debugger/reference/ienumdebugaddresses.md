---
title: "IEnumDebugAddresses | Microsoft Docs"
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
  - "IEnumDebugAddresses"
helpviewer_keywords: 
  - "IEnumDebugAddresses 介面"
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示實作的物件集合的[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
## 語法  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## 實作器注意事項  
 若要提供實作的物件集的符號提供者會實作這個介面[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  請注意這並非標準的 COM 列舉型別是否受限於[GetCount](../Topic/IEnumDebugAddresses::GetCount.md)方法。  
  
## 呼叫者的備忘稿  
 這個介面會傳回由[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)和[GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)。  
  
## 方法 Vtable 順序  
 這個介面會實作下列方法。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../Topic/IEnumDebugAddresses::Next.md)|擷取下的一組[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)列舉型別中的物件。|  
|[Skip](../Topic/IEnumDebugAddresses::Skip.md)|略過指定的數目的項目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|將重設第一個項目，為列舉型別。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|擷取一份目前的列舉型別。|  
|[GetCount](../Topic/IEnumDebugAddresses::GetCount.md)|擷取列舉型別中的項目數。|  
  
## 備註  
 偵錯引擎通常會使用這個介面來協助判斷適當的地址給運算式評估工具。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)