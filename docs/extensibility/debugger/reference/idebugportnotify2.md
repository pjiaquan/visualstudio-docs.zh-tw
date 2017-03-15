---
title: "IDebugPortNotify2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2"
helpviewer_keywords: 
  - "IDebugPortNotify2 介面"
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會登錄或解除登錄才能進行偵錯與連接埠執行的程式。  
  
## 語法  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者會實作這個介面以支援加入及移除連接埠的程式。  它通常會實作相同的物件實作[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面。  
  
## 呼叫者的備忘稿  
 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugPort2`介面會傳回這個介面。  此外，呼叫[GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md)會傳回這個介面。  偵錯引擎可以做為參數，以查看這個介面[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugPortNotify2`。  
  
|方法|描述|  
|--------|--------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|註冊連接埠執行的程式，才能進行偵錯。|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|從連接埠執行才能進行偵錯的程式會移除註冊。|  
  
## 備註  
 除非偵錯連接埠才有辦法知道程式的載入或卸載時，自訂的通訊埠供應商必須實作這個介面。  使用這個介面內會追蹤所有已載入偵錯通過特定連接埠的程式。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)