---
title: "IActiveScriptError::GetSourceLineText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourceLineText"
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourceLineText
擷取在發生錯誤之原始程式檔的線條，該指令碼引擎執行指令碼時。  
  
## 語法  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## 參數  
 `pbstrSourceLine`  
 \[out\] 接收原始程式碼行發生錯誤之緩衝區的位址。  
  
## 傳回值  
 傳回 `S_OK` ，如果成功或 `E_FAIL` ，如果原始程式檔中的程式碼行未擷取。  
  
## 請參閱  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)