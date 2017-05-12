---
title: "IActiveScriptSiteDebugEx 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx 介面"
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebugEx 介面
請使用 `IActiveScriptSiteDebug` 介面中實作這個介面，如果您正在撰寫需要取得執行階段錯誤告知在應用程式中的和選擇性地連結至應用程式以進行偵錯的主機。  如果第一個指令碼 Just\-In\-Time 偵錯工具在電腦上，找到同處理序偵錯管理員會將 `IActiveScriptDebug` 提供通知。  如果找不到 Just\-In\-Time 指令碼偵錯工具， PDM 傳遞 `IActiveScriptDebugEx` 提供通知。  
  
 若要取得執行階段錯誤的通知，您的主應用程式必須處理 [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/zh-tw/cf7639f9-a699-4571-9f3a-82ef52c0b5f4)。  根據使用者的動作，就可以決定將內部附加偵錯工具並傳回，或傳回開始 OnScriptErrorDebug `pfEnterDebugger` 參數的偵錯工具。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|在進行偵錯的處理常式找不到一部外部的 Just\-In\-Time 偵錯工具時，告知指令碼執行階段錯誤的主機。|