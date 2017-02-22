---
title: "IDebugDefaultPort2 | Microsoft Docs"
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
  - "IDebugDefaultPort2"
helpviewer_keywords: 
  - "IDebugDefaultPort2 介面"
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會提供幾種方法可以存取組件 」 的伺服器及通知功能。  
  
## 語法  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## 實作器注意事項  
 Visual Studio 會實作這個介面來代表用來存取程式的偵錯連接埠。  如果會處理遠端偵錯自訂的連接埠提供者也可以實作這個介面。  
  
## 呼叫者的備忘稿  
 引數上的方法[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面會提供這個介面。  呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面也可以取得這個介面。  
  
## 方法 Vtable 順序  
 除了中所定義的方法[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md)|取得從這個連接埠的連接埠的告知介面。|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|取得主控這個連接埠的伺服器介面。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|決定是否在本機電腦上執行此連接埠。|  
  
## 備註  
 名稱"`IDebugDefaultPort2`"是有點 misnomer，因為它不能代表預設的連接埠。  它可能會呼叫"IDebugPort3"。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)