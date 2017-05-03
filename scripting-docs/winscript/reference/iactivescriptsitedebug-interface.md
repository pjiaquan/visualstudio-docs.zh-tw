---
title: "IActiveScriptSiteDebug 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebug 介面"
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug 介面
智慧型主機實作介面 `IActiveScriptSiteDebug` 執行檔案管理和參與偵錯。  `IActiveScriptSite` 物件通常會提供 `IActiveScriptSiteDebug` 介面的實作。  若是如此，請呼叫方法 `IActiveScriptSite::QueryInterface` 取得 `IActiveScriptSiteDebug` 介面。  
  
 除了繼承自 `IUnknown` 的方法之外，`IActiveScriptSiteDebug` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|由語言引擎 `IDebugCodeContext::GetSourceContext`委派。|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|傳回應用程式進行偵錯的物件與這個指令碼網站。|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|取得下一個指令碼檔應該加入的應用程式節點。|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|允許智慧型主機決定如何處理執行階段錯誤。|