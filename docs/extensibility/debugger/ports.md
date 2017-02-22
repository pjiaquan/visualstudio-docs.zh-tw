---
title: "連接埠 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "通訊埠"
  - "偵錯 [偵錯 SDK]，連接埠"
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 連接埠
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯工具的架構的角度來看**連接埠**：  
  
-   伺服器上執行的處理程序的一組的容器。  例如，一個連接埠可能代表 Windows CE 為基礎的裝置，透過序列線或網路的非 DCOM 的電腦的連線。  一個特殊連接埠，稱為本機連接埠，會包含在本機電腦上執行的所有處理程序。  
  
-   可以識別其本身的名稱或識別項。  
  
-   可列舉的連接埠上執行的所有處理序啟動和終止這些處理程序。  
  
-   由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面，它由傳遞[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)引數為[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供處理所有 Windows 為主的程序，原生和 managed 的預設連接埠。  必須實作自訂的通訊埠連線，不是以 Windows 為基礎的外部裝置。  若要提供這種自訂的連接埠，自訂的連接埠提供者也必須實作。  
  
## 請參閱  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [處理序](../../extensibility/debugger/processes.md)   
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)