---
title: "IDebugApplicationNode100::SetFilterForEventSink | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::SetFilterForEventSink"
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::SetFilterForEventSink
設定在特定 [IDebugApplicationNodeEvents 介面](../../winscript/reference/idebugapplicationnodeevents-interface.md) 實作的篩選條件。  它允許指令碼偵錯工具會篩選掉編譯器產生的子應用程式節點，使 PDM 不再傳送事件，當這些建立或移除時。  根據預設，所有節點會傳送。  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md) 由 PDM v10.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```cpp  
HRESULT SetFilterForEventSink(  
        [in] DWORD dwCookie,  
        [in] APPLICATION_NODE_EVENT_FILTER filter  
        );  
  
```  
  
#### 參數  
 `dwCookie`  
 篩選條件的 Cookie。  
  
 `filter`  
 篩選器。  
  
## 請參閱  
 [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md)