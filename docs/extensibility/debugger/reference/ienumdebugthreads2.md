---
title: "IEnumDebugThreads2 | Microsoft Docs"
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
  - "IEnumDebugThreads2"
helpviewer_keywords: 
  - "IEnumDebugThreads2"
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個 interfac 列舉目前的偵錯工作階段中執行的執行緒。  
  
## 語法  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面表示一份在程式中的執行緒。  
  
## 呼叫者的備忘稿  
 呼叫[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)以取得這個介面表示一份所有處理序中執行的程式中的所有執行緒。  呼叫[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)以取得這個介面表示一份在程式中執行的執行緒。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugThreads2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../Topic/IEnumDebugThreads2::Next.md)|擷取指定的列舉型別序列中的執行緒數。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|略過指定的列舉型別序列中的執行緒數。|  
|[重設](../Topic/IEnumDebugThreads2::Reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|建立包含相同的列舉型別狀態與目前列舉值。|  
|[GetCount](../Topic/IEnumDebugThreads2::GetCount.md)|取得列舉值中的執行緒數目。|  
  
## 備註  
 Visual Studio 通常會取得這個介面來更新**執行緒**以取得清單中，第一個執行緒呼叫視窗也[執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)， [繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)，以及[逐步執行](../../../extensibility/debugger/reference/idebugprocess3-step.md)。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [逐步執行](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)