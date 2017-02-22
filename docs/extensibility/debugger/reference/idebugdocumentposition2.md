---
title: "IDebugDocumentPosition2 | Microsoft Docs"
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
  - "IDebugDocumentPosition2"
helpviewer_keywords: 
  - "IDebugDocumentPosition2 介面"
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會表示為抽象的位置，在原始程式檔中。  
  
## 語法  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## 實作器注意事項  
 Visual Studio 通常會實作這個介面。  如果它必須提供自己的原始程式碼，偵錯引擎 \(DE\) 也會實作這個介面 \(DE 實作的時機與[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面\)。  
  
## 呼叫者的備忘稿  
 這個介面，會當做引數傳入的[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)。  它也提供的一部分[BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)等位 \(具體來說， [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)結構\) 屬於依次[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構，用於建立暫止中斷點。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugDocumentPosition2`。  
  
|方法|描述|  
|--------|--------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|取得包含這個文件位置的原始程式檔的檔名。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|取得包含文件。|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|判斷指定的文件中若包含這個位置。|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|取得這個文件位置的範圍。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)