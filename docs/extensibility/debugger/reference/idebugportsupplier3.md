---
title: "IDebugPortSupplier3 | Microsoft Docs"
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
  - "IDebugPortSupplier3"
helpviewer_keywords: 
  - "IDebugPortSupplier3 介面"
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面允許呼叫端，以決定連接埠提供者是否可以保留連接埠 \(寫入磁碟\) 的偵錯工具的引動過程之間，並在之後會出現一份這些保留的連接埠。  
  
## 語法  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者會實作這個介面以支援保存或儲存至磁碟的連接埠資訊。  必須為相同的物件上實作這個介面[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)介面。  
  
## 呼叫者的備忘稿  
 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugPortSupplier2`以取得這個介面的介面。  
  
## 方法 Vtable 順序  
 除了從繼承的方法[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)介面，這個介面會支援下列：  
  
|方法|描述|  
|--------|--------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|傳回是否連接埠提供者可以保存的連接埠 \(藉由寫入磁碟\) 的偵錯工具的引動過程之間。|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|傳回物件，可用於列舉透過此連接埠提供者所寫回磁碟的所有連接埠。|  
  
## 備註  
 如果連接埠提供者可以保存在引動過程之間的連接埠，它應該實作這個介面。  當連接埠提供者為具現化，並且被終結的連接埠提供者時寫回磁碟，則應載入的連接埠。  
  
 偵錯引擎通常會不常使用的連接埠提供者，而且必須不需要用這個介面。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)