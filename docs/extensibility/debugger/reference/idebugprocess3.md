---
title: "IDebugProcess3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3"
helpviewer_keywords: 
  - "IDebugProcess3 介面"
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# IDebugProcess3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示處理程序和它的程式。  這個介面中的幾個方法的替代文字是用[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。  它提供處理序中的所有程式的控制權。  
  
> [!NOTE]
>  [繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md) [執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)，以及[逐步執行](../../../extensibility/debugger/reference/idebugprogram2-step.md)已取代的方法，和無法再使用。  使用對應的方法，在`IDebugProcess3`而是介面。  
  
## 語法  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## 實作器注意事項  
 實作這個介面是由管理程式，作為一組自訂的通訊埠供應商。  當群組方式管理程式時，您可以控制其執行，並建立一種語言的運算式評估工具。  藉由連接埠提供者，就必須實作這個介面。  
  
## 呼叫者的備忘稿  
 主要工作階段偵錯管理員 \(SDM\) 會呼叫這個介面以互動與一群這項程序中所識別的程式。  
  
 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)以取得這個介面的介面。  
  
## 方法 Vtable 順序  
 除了從繼承的方法[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)， `IDebugProcess3`實作下列的方法。  
  
|方法|描述|  
|--------|--------|  
|[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|繼續的執行或逐步執行處理程序。|  
|[執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|開始執行的處理序。|  
|[逐步執行](../../../extensibility/debugger/reference/idebugprocess3-step.md)|步驟轉寄一個指令或程序中的陳述式。|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|取得處理序已啟動偵錯的原因。|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|設定所控管的語言，以便偵錯引擎可以載入適當的運算式評估工具。|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|擷取目前為這項程序設定的語言。|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|停用編輯後繼續 \(ENC\)，此處理程序。<br /><br /> 自訂的連接埠提供者未實作這個方法 \(應該永遠傳回`E_NOTIMPL`\)。|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|此程序可獲得 ENC 狀態。<br /><br /> 自訂的連接埠提供者未實作這個方法 \(應該永遠傳回`E_NOTIMPL`\)。|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|擷取可用的偵錯引擎的唯一識別項的陣列。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)