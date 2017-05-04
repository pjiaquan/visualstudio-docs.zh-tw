---
title: "IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld::ParseProcedureText"
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld::ParseProcedureText
解析指定編碼程序並將匿名程序加入至命名空間。  
  
## 語法  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### 參數  
 `pstrCode`  
 \[in\] 要評估的程式文字。  這個字串解譯為而定的指令碼語言。  
  
 `pstrFormalParams`  
 \[in\] 型式參數名稱的程序。  必須分開參數名稱與指令碼引擎的適當的符號。  不應該括在括號中的名稱。  
  
 `pstrItemName`  
 \[in\] 要寫入內容程序要評估具名項目的名稱。  如果此參數為 `NULL`，程式碼在指令碼引擎的全域內容進行評估。  
  
 `punkContext`  
 \[in\] 內容物件。  這個物件是保留在偵錯環境，這種內容可能由偵錯工具提供表示現用執行階段內容。  如果此參數為， `NULL`引擎使用 `pstrItemName` 識別內容。  
  
 `pstrDelimiter`  
 \[in\] 結束程序符號。  當 `pstrCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如，兩個單引號 \("\)，偵測程序的結尾。  這個參數指定 \(例如使用的主機，允許指令碼引擎提供了一些條件，原始前置處理符號 \(，取代使用單引號 \(『\) 與兩個單引號做為分隔符號\)。  \(和\)，如果指令碼引擎正確方式使用這項資訊決定指令碼引擎。  如果未使用分隔符號指示的關閉程序，請將這個參數設定為 `NULL` 。  
  
 `dwSourceContextCookie`  
 \[in\] 使用於偵錯用途的應用程式定義的值。  
  
 `ulStartingLineNumber`  
 \[in\] 指定中以零起始的值解析哪一行開始。  
  
 `dwFlags`  
 \[in\] 旗標與程序。  可以是下列值的組合。  
  
|常數|值|意義|  
|--------|-------|--------|  
|SCRIPTPROC\_ISEXPRESSION|0x00000020|表示 `pstrCode` 的程式碼是表示程序之傳回值的運算式。|  
|SCRIPTPROC\_IMPLICIT\_THIS|0x00000100|表示 `this` 指標會併入程序範圍內。|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|0x00000200|表示 `this` 指標的父代 \(Parent\) 是包含在程序的範圍內。|  
  
 `ppdisp`  
 \[in\] 傳回預設方法是此方法所剖析之程序的分派包裝函式。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_NOTIMPL`|不支援這個方法。  指令碼引擎不支援程序的執行階段加入至命名空間。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎會處於未初始化或關閉狀態\)。|  
|`OLESCRIPT_E_SYNTAX`|未指定中的語法錯誤在程序中。|  
|`S_FALSE`|指令碼引擎不支援分派物件; `ppdisp`參數設定為 `NULL`。|  
  
## 備註  
 在呼叫期間，指令碼不會評估，相反地，會編譯成可從指令碼呼叫之後的 `ppdisp` 的方法。  
  
 這個介面已被取代而建議使用 `IActiveScriptParseProcedure` 介面。  `IActiveScriptParseProcedure::ParseProcedureText` 相似的方法，這個方法，但是這個處理序名稱指定。  在所有情況下，應該使用 `IActiveScriptParseProcedure::ParseProcedureText` 。  
  
## 請參閱  
 [IActiveScriptParseProcedureOld 介面](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)