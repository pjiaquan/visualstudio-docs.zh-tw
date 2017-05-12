---
title: "IActiveScriptErrorDebug 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug 介面"
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug 介面
在編譯時期錯誤和執行階段例外狀況提供文件內容資訊。  `IActiveScriptError::QueryInterface` `IActiveScriptErrorDebug` 方法支援介面。  
  
 除了繼承自 `IActiveScriptError` 的方法之外，`IActiveScriptErrorDebug` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|針對這個錯誤的文件內容。|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|提供實際用於執行階段錯誤的堆疊框架。|