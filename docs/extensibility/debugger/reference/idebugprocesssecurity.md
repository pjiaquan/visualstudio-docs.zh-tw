---
title: "IDebugProcessSecurity | Microsoft Docs"
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
  - "IDebugProcessSecurity 介面"
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`IDebugProcessSecurity`警告使用者附加至處理序並不安全的連接埠提供者來執行。  
  
## 語法  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProcessSecurity`。  
  
|方法|描述|  
|--------|--------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|從連接埠提供者取得使用者名稱。|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|附加至偵錯的處理序並不安全，警告使用者。|  
  
## 備註  
 實作這個介面來顯示一個警告訊息，並允許使用者取消，如果您要連接的程序可視為不安全。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [連接埠](../../../extensibility/debugger/ports.md)   
 [連接埠供應商](../../../extensibility/debugger/port-suppliers.md)   
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)