---
title: "IDebugApplication110 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110 介面"
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110 介面
`IDebugApplication110` 介面 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)擴充的功能。  您可以呼叫 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)之實作的 QueryInterface 取得此介面的執行個體。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 方法  
 `IDebugApplication110` 介面公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|在主執行緒上進行同步呼叫。|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|在主執行緒進行非同步呼叫。|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|等候任何指定的控制代碼都收到信號時，允許跨執行緒呼叫張貼至這個執行緒時。  必須從偵錯工具執行緒呼叫這個方法。|