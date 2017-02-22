---
title: "IDebugDocumentText2 | Microsoft Docs"
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
  - "IDebugDocumentText2"
helpviewer_keywords: 
  - "IDebugDocumentText2 介面"
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示文字文件。  
  
## 語法  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## 實作器注意事項  
 以文字形式提供所需的原始程式碼時，偵錯引擎 \(DE\) 會實作這個介面。  因為如果將 DE 實作，這是最常見的情況下， [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面，它也應該實作`IDebugDocumentText2`介面。  
  
## 呼叫者的備忘稿  
 使用`QueryInterface`方法，以取得這個介面，從`IDebugDocument2`介面。  
  
## 方法 Vtable 順序  
 除了在方法`IDebugDocument2`介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|擷取文件中的該位置的文字大小。|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|從指定的位置，文件中擷取的文字。|  
  
## 備註  
 實作這個介面的物件也必須實作<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面，哪些材料<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>之介面[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)物件。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)