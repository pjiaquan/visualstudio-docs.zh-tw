---
title: "IDebugPortSupplierEx2 | Microsoft Docs"
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
  - "IDebugPortSupplierEx2 介面"
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplierEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

提供支援的通訊埠供應商，以選取並與其互動的核心的伺服器。  
  
## 語法  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者會實作這個介面，這樣就可以選擇要使用的核心伺服器。  
  
## 方法  
 下表顯示的方法 **IDebugPortSupplierEx2**。  
  
|方法|描述|  
|--------|--------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|設定連接埠提供者的核心的伺服器。|  
  
## 需求  
 標頭: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)