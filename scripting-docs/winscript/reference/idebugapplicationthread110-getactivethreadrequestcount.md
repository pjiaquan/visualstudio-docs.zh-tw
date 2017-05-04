---
title: "IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::GetActiveThreadRequestCount"
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugApplicationThread110::GetActiveThreadRequestCount
會傳回執行緒要求數目從目前正在處理的 PDM 的執行緒切換機制的。  這個數字通常是 0 或 1。  不過，這個數字可能較高，如果處理一執行緒呼叫的開頭，但是觸發同步呼叫的執行緒或暫止執行緒並允許傳入呼叫會重新處理 \(例如，藉由觸發 [IRemoteDebugApplicationEvents 介面](../../winscript/reference/iremotedebugapplicationevents-interface.md) 事件，在偵錯工具執行緒上執行\)。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md) 由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
  
```  
  
#### 參數  
 `puiThreadRequests`  
 \[in\] 執行緒的要求數。  
  
## 請參閱  
 [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)