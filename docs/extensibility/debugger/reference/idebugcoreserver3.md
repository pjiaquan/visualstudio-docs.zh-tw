---
title: "IDebugCoreServer3 | Microsoft Docs"
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
  - "IDebugCoreServer3"
helpviewer_keywords: 
  - "IDebugCoreServer3 介面"
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面可讓的伺服器處理序正在執行中的相關資訊的存取。  
  
## 語法  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## 實作器注意事項  
 Visual Studio 會實作這個介面。  
  
## 呼叫者的備忘稿  
 使用[QueryInterface](/visual-cpp/atl/queryinterface)以取得這個介面，從[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面。  呼叫[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)也可將傳回這個介面。  這個介面是最常使用自訂的通訊埠供應商所啟動 \(本機或遠端\) 伺服器上的程式。  
  
## 方法 Vtable 順序  
 除了在方法[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|擷取伺服器的名稱。|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|擷取的好記的版本，伺服器名稱|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|指示要這些處理序啟動時，會自動附加至處理序的詳盡的偵錯引擎。|  
|[DiagnoseWebDebuggingError](../Topic/IDebugCoreServer3::DiagnoseWebDebuggingError.md)|自動附加失敗時，擷取特定的錯誤碼。|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|伺服器上建立偵錯引擎執行的個體。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|會擷取旗標，表示伺服器是否為與呼叫者相同的電腦上。|  
|[GetConnectionProtocol](../Topic/IDebugCoreServer3::GetConnectionProtocol.md)|擷取值，指出用來與伺服器通訊的通訊協定。|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|停用所有自動都附加這台伺服器所知的所有偵錯引擎的設定。|  
  
## 備註  
 自訂通訊埠供應商收到[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面上呼叫[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)。  `IDebugCoreServer3`介面可以取自該介面。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)