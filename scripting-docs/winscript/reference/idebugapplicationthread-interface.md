---
title: "IDebugApplicationThread 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread 介面"
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread 介面
讓語言引擎，並提供執行緒同步處理和維護執行緒特定的主應用程式的偵錯狀態資訊。  這個介面會擴充介面 `IRemoteDebugApplicationThread` 提供非遠端存取執行緒。  
  
 除了繼承自 `IRemoteDebugApplicationThread` 的方法之外，`IDebugApplicationThread` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|為呼叫端提供一種機制。在應用程式執行緒上執行程式碼。|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|判斷這個執行緒是目前執行的執行緒。|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|判斷這個執行緒是偵錯工具執行緒。|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|將這個執行緒的描述。|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|將執行緒狀態的描述。|