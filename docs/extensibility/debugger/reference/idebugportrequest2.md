---
title: "IDebugPortRequest2 | Microsoft Docs"
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
  - "IDebugPortRequest2"
helpviewer_keywords: 
  - "IDebugPortRequest2 介面"
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會描述連接埠。  這項描述用來加入連接埠提供者的連接埠。  
  
## 語法  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## 實作器注意事項  
 Visual Studio 通常會實作這個介面，從連接埠提供者取得偵錯連接埠的處理序中。  
  
## 呼叫者的備忘稿  
 這個介面會傳遞至[下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)來建立偵錯連接埠。  呼叫[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)會傳回這個介面，代表用來在第一時間內建立的連接埠的要求。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugPortRequest2`。  
  
|方法|描述|  
|--------|--------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|取得要建立的連接埠的名稱。|  
  
## 備註  
 偵錯引擎通常會不常使用的連接埠提供者，而且必須不需要用這個介面。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)