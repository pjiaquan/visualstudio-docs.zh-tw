---
title: "IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference"
ms.assetid: fcf60971-9518-4b24-a3a6-1e2e30a02cea
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
如果有傳回 Windows 執行階段限制的參考錯誤。  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) 由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```cpp  
HRESULT GetRestrictedErrorReference([out] BSTR * referenceString);  
```  
  
#### 參數  
 `referenceString`  
 \[in\] 參考錯誤字串。  
  
## 請參閱  
 [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)