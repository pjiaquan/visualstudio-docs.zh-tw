---
title: "IDebugDocument2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2"
helpviewer_keywords: 
  - "IDebugDocument2 介面"
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocument2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示來源文件。  
  
## 語法  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## 實作器注意事項  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]通常會實作這個介面。  它必須提供原始程式檔和來源不存在磁碟上時，偵錯引擎 \(DE\) 也可以實作這個介面。  在這種情況下，還實作 DE [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)和[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)介面，以及一些其他的方法，在[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)和[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)介面。  
  
## 呼叫者的備忘稿  
 上的方法`IDebugDocumentContext2`， `IDebugDisassemblyStream2`， `IDebugDocumentPosition2`，以及`IDebugActivateDocumentEvent2`介面傳回這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugDocument2`。  
  
|方法|描述|  
|--------|--------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|取得其中數個表單中的文件的名稱。|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|取得文件的類別識別項。|  
  
## 備註  
 只有在 DE 提供原始程式碼時，只會實作這個介面。  比方說，當您正在偵錯的 HTML 網頁上的指令碼，DE 提供原始程式碼因為來源下載或以動態方式產生，並不是磁碟檔案。  當偵錯傳統的語言，例如 c \+ \+ 中，這個介面就不需要實作。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)   
 [GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)