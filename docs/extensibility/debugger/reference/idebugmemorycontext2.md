---
title: "IDebugMemoryContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2"
helpviewer_keywords: 
  - "IDebugMemoryContext2 介面"
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示執行程式的偵錯的電腦的位址空間中的位置。  
  
## 語法  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面表示記憶體中的地址。  
  
## 呼叫者的備忘稿  
 呼叫[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)或[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)會傳回這個介面。  此外，要呼叫的方法[Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)和[差集](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)套用適當的算術運算後傳回這個介面的新複本。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugMemoryContext2`。  
  
|方法|描述|  
|--------|--------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|取得此內容的使用者可顯示的名稱。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|取得描述這個內容的資訊。|  
|[Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|將指定的值加入至目前的內容的位址，來建立新的內容中。|  
|[差集](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|四元數減去指定的值，從目前的內容的位址，來建立新的內容。|  
|[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|比較兩個內容的方式由比較旗標。|  
  
## 備註  
 Visual Studio **的記憶體**的視窗呼叫[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)以取得`IDebugMemoryContext2` ，其中包含評估的運算式所使用的記憶體位址的介面。  此內容會接著傳遞給[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)和[WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md)來指定要讀取或寫入的地址。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md)