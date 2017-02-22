---
title: "呼叫堆疊評估 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK]，呼叫堆疊評估"
  - "呼叫堆疊、 評估"
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 呼叫堆疊評估
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

若要檢視呼叫堆疊的堆疊框架，在中斷模式期間，您必須實作[EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)方法。  
  
## 評估的方法  
 對於簡單的偵錯引擎 \(DE\)，則可能是只有一個堆疊框架。  若要檢查的堆疊框架，在中斷模式期間，您必須實作下列的方法[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)。  
  
|方法|描述|  
|--------|--------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|取得堆疊框架中的程式碼內容。  程式碼內容表示目前堆疊框架中的指令指標。|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|取得堆疊框架中的文件內容。  文件內容表示目前堆疊框架的原始碼的位置。  檢視原始程式碼，您會在程式停止時的必要項。|  
  
 這些方法需要數個內容相關的介面和方法的實作。  因此，您必須實作[GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)方法，下列的方法[IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)。  
  
|方法|描述|  
|--------|--------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|取得檔案陳述式的範圍的文件內容。|  
  
 若要列舉程式碼內容，您必須實作所有方法的[IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)。  
  
## 請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)