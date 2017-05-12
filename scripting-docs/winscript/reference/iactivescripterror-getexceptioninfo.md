---
title: "IActiveScriptError::GetExceptionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetExceptionInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetExceptionInfo"
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetExceptionInfo
擷取所發生之錯誤的相關資訊，該指令碼引擎執行指令碼時。  
  
## 語法  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### 參數  
 `pexcepinfo`  
 \[in\] 要取得錯誤訊息 `EXCEPINFO` 結構的位址。  
  
## 傳回值  
 傳回 `S_OK` ，如果成功或 `E_FAIL` ，如果發生錯誤則為。  
  
## 請參閱  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)