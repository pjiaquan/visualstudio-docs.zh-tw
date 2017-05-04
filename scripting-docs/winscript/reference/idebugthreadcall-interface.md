---
title: "IDebugThreadCall 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugThreadCall 介面"
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugThreadCall 介面
`IDebugThreadCall` 介面而不使用封送處理實作的 `IDebugThread` 的跨執行緒呼叫提供是同處理序偵錯 Manager \(PDM\) 的元件通常會實作。  
  
 PDM 呼叫所需的執行緒的 `IDebugThreadCall` 介面， `IDebugThreadCall` 分派介面，而這個呼叫所實作。  `IDebugThreadCall` 介面轉型為參數傳遞的參數資訊給適當的頂端。  
  
 `IDebugThreadCall` 介面是無限制執行緒的物件。  
  
## 方法  
 除了繼承自 `IUnknown` 的方法之外，`IDebugThreadCall` 介面還會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|在另一個執行緒的程式碼呼叫。|