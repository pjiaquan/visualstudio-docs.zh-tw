---
title: "IDebugBeforeSymbolSearchEvent2 | Microsoft Docs"
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
  - "IDebugBeforeSymbolSearchEvent2 介面"
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

偵錯引擎 \(DE\) 這個介面過程中傳送至工作階段偵錯管理員 \(SDM\) 設定的狀態訊息列符號載入。  
  
## 語法  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 當它必須設定狀態列訊息符號載入期間，DE 會實作這個介面。  繼續使用，或是部份中的指令碼直譯器的偵錯引擎只會實作這個介面。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件 \(使用 SDM  **QueryInterface** 存取 **IDebugEvent2** 介面\)。  
  
## 呼叫者的備忘稿  
 DE 建立，並當它必須設定狀態列訊息符號載入時，會傳送這個事件的物件。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，由 SDM 提供的回呼函式。  
  
## 方法  
 下表顯示的方法`IDebugBeforeSymbolSearchEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|擷取目前正在進行偵錯模組的名稱。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll