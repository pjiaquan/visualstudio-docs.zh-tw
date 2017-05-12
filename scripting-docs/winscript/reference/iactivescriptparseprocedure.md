---
title: "IActiveScriptParseProcedure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParseProcedure 介面"
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure
如果視窗指令碼引擎允許程序的原始程式碼文字加入至指令碼，就會實作介面 `IActiveScriptParseProcedure` 。  對於沒有獨立建立的環境，例如 VBScript 的解譯的指令碼語言，這提供替代機制 \(除了以外 `IPersist``IActiveScriptParse` 或\*\) 將指令碼程序加入至命名空間。  
  
## 依照 Vtable 順序的方法  
  
|||  
|-|-|  
|方法|描述|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|解析指定編碼程序和程序加入至命名空間。|  
  
## 請參閱  
 [動態指令碼的介面](../../winscript/reference/active-script-interfaces.md)