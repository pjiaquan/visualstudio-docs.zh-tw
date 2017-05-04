---
title: "IActiveScriptWinRTErrorDebug 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug 介面"
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptWinRTErrorDebug 介面
實作由 JavaScript 引擎提供從 [BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md) 事件的擴充 Windows 執行階段執行錯誤訊息。  您可以 [IActiveScriptError](../../winscript/reference/iactivescripterror.md) QueryInterface 從物件取得它。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 方法  
 `IActiveScriptWinRTErrorDebug` 介面公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|如果有傳回 Windows 執行階段執行階段錯誤的 SID，這些功能。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|如果有傳回 Windows 執行階段限制的錯誤參考字串。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|如果有傳回 Windows 執行階段限制的錯誤字串。|