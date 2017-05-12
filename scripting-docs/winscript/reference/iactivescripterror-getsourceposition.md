---
title: "IActiveScriptError::GetSourcePosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourcePosition"
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourcePosition
擷取錯誤原始程式碼的位置，當指令碼引擎執行指令碼時。  
  
## 語法  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### 參數  
 `pdwSourceContext`  
 \[out\] 接收 Cookie 識別內容變數的位址。  這個參數的說明取決於主應用程式。  
  
 `pulLineNumber`  
 \[out\] 接收在原始程式檔中的行號錯誤變數的位址。  
  
 `pichCharPosition`  
 \[out\] 會接收該行的字元位置錯誤變數的位址。  
  
## 傳回值  
 傳回 `S_OK` ，如果成功或 `E_FAIL` ，如果位置並未被擷取。  
  
## 請參閱  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)