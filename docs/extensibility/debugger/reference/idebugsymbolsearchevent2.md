---
title: "IDebugSymbolSearchEvent2 | Microsoft Docs"
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
  - "IDebugSymbolSearchEvent2"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2"
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會傳送偵錯引擎 \(DE\) 來表示所偵錯模組的偵錯符號都已載入。  
  
## 語法  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面來報告已載入模組的符號。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## 呼叫者的備忘稿  
 DE 建立並傳送報告已載入模組的符號這個事件物件。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## 方法 Vtable 順序  
 `IDebugSymbolSearchEvent2`介面會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|擷取的符號搜尋結果的相關資訊。|  
  
## 備註  
 即使無法載入符號時，就會傳送這個事件。  呼叫`IDebugSymbolSearchEvent2::GetSymbolSearchInfo`可讓此事件處理常式可以判斷是否該模組實際上會有任何符號。  
  
 Visual Studio 的通常是利用這個事件來更新的狀態中的已載入符號的**模組**視窗。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)