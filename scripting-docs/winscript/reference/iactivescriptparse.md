---
title: "IActiveScriptParse | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParse 介面"
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse
如果視窗指令碼引擎允許原始文字 Scriptlet 程式碼加入至指令碼或允許運算式文字會在執行階段，會實作介面 `IActiveScriptParse` 。  對於沒有獨立建立的環境，例如 VBScript 的解譯的指令碼語言，這提供替代機制 \(除了以外\) `IPersist*`讓指令碼輸入指令碼引擎和指令碼片段附加至各種物件事件。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|初始化指令碼引擎。|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|將程式碼加入至 scriptlet 指令碼。|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|剖析指定的程式碼 scriptlet，宣告加入至命名空間和評估程式碼適當。|  
  
## 請參閱  
 [動態指令碼的介面](../../winscript/reference/active-script-interfaces.md)