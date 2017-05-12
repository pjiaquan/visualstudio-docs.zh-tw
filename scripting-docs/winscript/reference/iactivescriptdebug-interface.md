---
title: "IActiveScriptDebug 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptDebug 介面"
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug 介面
實作支援偵錯的指令碼引擎。  一般而言，實作的物件 `IActiveScriptDebug` 介面也會實作介面 `IActiveScript` 。  如果是這種情況，請呼叫方法 `IActiveScript::QueryInterface` 取得 `IActiveScriptDebug` 介面。  
  
 `IActiveScriptDebug` 介面提供方法用來:  
  
-   接收檔案管理智慧型主機。  
  
-   同處理序偵錯多個處理常式同步指令碼引擎偵錯。  
  
 除了繼承自 `IUnknown` 的方法之外，`IActiveScriptDebug` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|傳回指令碼任意文字區塊的文字屬性變更為。|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|傳回隨機 scriptlet 文字屬性。|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|`IDebugDocumentContext::EnumCodeContexts`的委派。|