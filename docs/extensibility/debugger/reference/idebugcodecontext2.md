---
title: "IDebugCodeContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2"
helpviewer_keywords: 
  - "IDebugCodeContext2 介面"
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示程式碼指示的起始位置。  大部分的執行階段架構的今天，程式碼內容可以視為該應用程式的執行資料流中的地址。  
  
## 語法  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## 實作器注意事項  
 偵錯引擎實作這個介面來關聯到文件位置的程式碼指示的位置。  
  
## 呼叫者的備忘稿  
 在許多介面上的方法會傳回這個介面，更常見的是， [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)。  它也可以用廣泛與[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)介面以及在 \[中斷點解析資訊。  
  
## 方法 Vtable 順序  
 除了在方法[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)|取得相對於現用的程式碼內容的文件內容。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|取得這個程式碼內容的語言資訊。|  
  
## 備註  
 主要差別`IDebugCodeContext2`介面和[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面是`IDebugCodeContext2`永遠指示對齊。  這表示`IDebugCodeContext2`永遠指向開頭的指令，而`IDebugMemoryContext2`也會指出在執行階段架構的記憶體的任何位元組。  `IDebugCodeContext2`根據指示，而不是由最基本的儲存區大小 \(通常為位元組\)，就會增加。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../Topic/IDebugThread2::CanSetNextStatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)