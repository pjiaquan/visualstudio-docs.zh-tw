---
title: "IDebugDocumentContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2"
helpviewer_keywords: 
  - "IDebugDocumentContext2"
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocumentContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示來源檔案的文件中的位置。  
  
## 語法  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面支援層級來源的程式碼的偵錯的一部分。  除了在原始程式碼中的位置，這個介面會提供方法來比較內容，並瀏覽原始程式碼文件。  
  
## 呼叫者的備忘稿  
 方法在多次的介面，更常見的是[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)和[GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)介面，傳回這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugDocumentContext2`。  
  
|方法|描述|  
|--------|--------|  
|[GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)|取得包含此文件內容的文件。|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|取得包含此文件內容的文件的可顯示的名稱。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|擷取一份與這個文件內容相關聯的所有程式碼內容。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|取得與這個文件內容相關聯的語言。|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|取得檔案陳述式範圍的本文中的文件。|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|取得檔案的來源範圍的本文中的文件。|  
|[比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|比較這個文件內容，以指定之陣列的文件內容。|  
|[搜尋](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|將文件內容移動指定的陳述式或程式行數。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)