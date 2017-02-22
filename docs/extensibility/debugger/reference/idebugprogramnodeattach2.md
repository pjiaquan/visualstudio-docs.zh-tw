---
title: "IDebugProgramNodeAttach2 | Microsoft Docs"
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
  - "IDebugProgramNodeAttach2"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2 介面"
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

允許嘗試附加至相關聯的程式，接受通知的程式\] 節點。  
  
## 語法  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## 實作器注意事項  
 實作相同類別上實作這個介面[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)介面，以接收附加作業的通知，並提供取消附加作業的機會。  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫`QueryInterface`中的方法[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件。  [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)之前，必須呼叫方法[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法，以提供程式\] 節點來停止附加的處理序的機會。  
  
## 方法 Vtable 順序  
 這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|將附加至相關聯的程式，或聽從附加處理序[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。|  
  
## 備註  
 這個介面是慣用的替代方式，來取代[Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)方法。  所有的偵錯引擎會永遠載入與`CoCreateInstance`函式，也就是它們會之外具現化偵錯程式的位址空間。  
  
 如果先前的實作的`IDebugProgramNode2::Attach_V7`方法不只要設定`GUID`正在偵錯程式，然後只[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)必須實作的方法。  
  
 如果先前的實作的`IDebugProgramNode2::Attach_V7`使用所提供的回呼介面的方法，那麼該功能必須移至的實作[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法，並`IDebugProgramNodeAttach2`介面並沒有實作。  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)