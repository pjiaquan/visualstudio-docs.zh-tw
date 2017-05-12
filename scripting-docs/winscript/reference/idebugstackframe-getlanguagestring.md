---
title: "IDebugStackFrame::GetLanguageString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetLanguageString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetLanguageString"
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetLanguageString
傳回這種語言中的簡短或完整的文字描述。  
  
## 語法  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### 參數  
 `fLong`  
 \[in\] 旗標，請 `TRUE` 傳回其中一個長的描述，並傳回 `FALSE` 簡短描述。  
  
 `pbstrLanguage`  
 \[in\] 語言的描述。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 通常，如果是， `fLong` `FALSE`，這個方法可提供這個語言的名稱與堆疊框架。  當 `fLong` 是 `TRUE`時，這個方法可能會提供完整的產品文件。  
  
## 請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)