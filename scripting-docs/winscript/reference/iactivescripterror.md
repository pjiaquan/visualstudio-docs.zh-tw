---
title: "IActiveScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptError 介面"
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError
實作這個介面的物件傳遞至方法 [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) ，每當指令碼引擎遇到未處理的錯誤。  主應用程式會呼叫這個物件的方法來取得已發生之錯誤的資訊。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|擷取關於錯誤的資訊。|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|擷取錯誤原始程式碼的位置。|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|擷取在發生錯誤的來源文件中的行。|  
  
## 請參閱  
 [動態指令碼的介面](../../winscript/reference/active-script-interfaces.md)