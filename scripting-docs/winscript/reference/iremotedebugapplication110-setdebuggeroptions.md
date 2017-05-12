---
title: "IRemoteDebugApplication110::SetDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::SetDebuggerOptions"
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::SetDebuggerOptions
呼叫更新偵錯工具選項。  應該在 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)之後呼叫這個方法。  [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) 方法自動重設為預設選項。  選項會預設為 0 \(SDO\_NONE\)。  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md) 由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```cpp  
HRESULT SetDebuggerOptions(  
        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,  
        [in] enum SCRIPT_DEBUGGER_OPTIONS value  
    );  
  
```  
  
#### 參數  
 `mask`  
 [SCRIPT\_DEBUGGER\_OPTIONS 列舉](../../winscript/reference/script-debugger-options-enumeration.md) 遮罩。  
  
 `value`  
 [SCRIPT\_DEBUGGER\_OPTIONS 列舉](../../winscript/reference/script-debugger-options-enumeration.md) 值。  
  
## 請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 介面](../../winscript/reference/iremotedebugapplication110-interface.md)