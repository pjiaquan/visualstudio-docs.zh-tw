---
title: "IDebugProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2"
helpviewer_keywords: 
  - "IDebugProgramNode2 介面"
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示一種程式，才能進行偵錯。  
  
## 語法  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 或自訂的連接埠提供者實作這個介面表示一種程式，才能進行偵錯。  通常會實作這個介面上實作的同一個物件[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。  這個介面登錄與[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]藉由呼叫[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)。  
  
## 呼叫者的備忘稿  
 呼叫[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) ，傳回這個介面。  自訂的連接埠提供者會收到這個介面，透過呼叫[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。  將 DE 接收這個介面，透過呼叫[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProgramNode2`。  
  
|方法|描述|  
|--------|--------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|取得程式的名稱。|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|取得裝載程式的處理序的名稱。|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|取得裝載程式的處理序中的系統處理序識別項。|  
|[GetHostMachineName\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|被取代。  請勿使用。|  
|[Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|被取代。  請勿使用。  請參閱[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)另一個方法的介面。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|取得名稱和執行這個程式 DE 的識別項。|  
|[DetachDebugger\_V7](../Topic/IDebugProgramNode2::DetachDebugger_V7.md)|被取代。  請勿使用。|  
  
## 備註  
 工作階段偵錯管理員 \(SDM\) 通常會呼叫[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)以取得這個介面。  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)