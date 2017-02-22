---
title: "IDebugProgramEx2 | Microsoft Docs"
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
  - "IDebugProgramEx2"
helpviewer_keywords: 
  - "IDebugProgramEx2 介面"
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會讓工作階段偵錯管理員 \(SDM\) 附加至程式，並取得與程式相關的 \[程式\] 節點。  
  
## 語法  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者以相同的物件上實作這個介面[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面，為了讓 SDM 附加至程式，而同時允許連接埠提供者，來追蹤所有的工作階段附加至程式。  如果選擇自訂的連接埠提供者就可以實作這個介面。  
  
## 呼叫者的備忘稿  
 SDM 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugProgram2`以取得這個介面來追蹤工作階段附加至程式的介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProgramEx2`。  
  
|方法|描述|  
|--------|--------|  
|[附加](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|將程式附加到工作階段。|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|取得與程式相關的 \[程式\] 節點。|  
  
## 備註  
 這個介面是私用 SDM 和程式之間。  
  
## 需求  
 標頭: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)