---
title: "IDebugPort2 | Microsoft Docs"
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
  - "IDebugPort2"
helpviewer_keywords: 
  - "IDebugPort2 介面"
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示在機器上的偵錯連接埠。  
  
## 語法  
  
```  
IDebugPort2 : IUnknown  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者會實作這個介面來代表電腦上的偵錯連接埠。  
  
 如果連接埠支援傳送連接埠的事件，它也必須實作<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面以支援<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面，進而提供[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)介面。  
  
## 呼叫者的備忘稿  
 要呼叫的方法[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)或[下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)傳回這個介面，表示要求的連接埠。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugPort2`。  
  
|方法|描述|  
|--------|--------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|傳回連接埠名稱。|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|傳回連接埠識別項。|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|會將用來建立連接埠 \(若有\) 的要求。|  
|[GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)|傳回這個連接埠的連接埠提供者。|  
|[GetProcess](../Topic/IDebugPort2::GetProcess.md)|傳回指定處理序的識別項的處理序的介面。|  
|[EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)|列舉連接埠上執行的所有處理程序。|  
  
## 備註  
 本機連接埠可存取所有的處理程序與本機電腦上執行的程式。  Windows CE 為基礎的裝置，來建立序列電纜連線或網路連線到非 DCOM 的電腦，可能表示其他連接埠。  `IDebugPort2`介面用來找出的名稱和識別項的連接埠，列舉所有的連接埠上執行的處理程序，並提供設備，啟動和結束連接埠上的處理序。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)