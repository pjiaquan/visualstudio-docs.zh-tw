---
title: "IActiveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScript 介面"
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript
提供必要的方法會初始化指令碼引擎。  指令碼引擎必須實作介面 `IActiveScript` 。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|告知主應用程式所提供的指令碼引擎 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 網站。|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|擷取站台物件與視窗指令碼引擎。|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|將指令碼引擎讀入指定的狀態。|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|擷取指令碼引擎的目前狀態。|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|使指令碼引擎會放棄所有目前載入的指令碼，會遺失必須其他物件之狀態和釋放任何介面指標，因此輸入已關閉狀態。|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|加入根層級項目的名稱加入至指令碼引擎的命名空間。|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|將型別程式庫加入至指令碼的命名空間。|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|擷取執行指令碼的 `IDispatch` 介面。|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|擷取目前執行中的執行緒上的指令碼引擎中定義的識別項。|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|擷取執行緒的指令碼引擎中定義的識別項與特定的 Microsoft Win32 執行緒。|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|擷取指令碼執行緒目前的狀態。|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|會中斷執行指令碼執行緒執行。|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|複製目前指令碼引擎 \(減去任何目前執行狀態\)，傳回沒有網站在目前執行緒上載入的指令碼引擎。|  
  
## 請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)