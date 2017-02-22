---
title: "IDebugAddress | Microsoft Docs"
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
  - "IDebugAddress"
helpviewer_keywords: 
  - "IDebugAddress 介面"
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示某個項目的位址。  它會傳回符號處理常式。  
  
## 語法  
  
```  
IDebugAddress : IUnknown  
```  
  
## 實作器注意事項  
 符號提供者會實作這個介面來代表物件的位址。  
  
## 呼叫者的備忘稿  
 許多介面上的許多方法會傳回這個介面。  
  
## 方法 Vtable 順序  
 這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|擷取[DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構描述物件和它的位置。|  
  
## 備註  
 符號提供者會傳回這個介面來代表物件和它的位置，在特定的範圍 \(例如，函式、 方法或類別\)。  這個介面是從傳回，且會傳遞的符號提供者和運算式的各種方法來評估工具。  一般來說，符號的提供者可解譯這個介面的內容所需要的唯一實體。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)