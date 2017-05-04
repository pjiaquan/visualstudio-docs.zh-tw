---
title: "IRemoteDebugApplication110 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110 介面"
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IRemoteDebugApplication110 介面
用來提供可以透過指令碼偵錯之處理序呼叫端呼叫的新功能。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 方法  
 `IRemoteDebugApplication110` 介面公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|呼叫更新偵錯工具選項。  選項會預設為 0 \(SDO\_NONE\)。|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|傳回目前啟用的選項集。|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|傳回呼叫的 SetSite 主應用程式的主執行緒。|