---
title: "IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedure_ParseProcedureText"
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure::ParseProcedureText
解析指定編碼程序並加入程序加入至命名空間。  
  
## 語法  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### 參數  
 `pstrCode`  
 \[in\] 要評估的程式文字的位址。  這個字串解譯為而定的指令碼語言。  
  
 `pstrFormalParams`  
 \[in\] 型式參數名稱位址對於程序。  必須分開參數名稱與指令碼引擎的適當的符號。  不應該括在括號中的名稱。  
  
 `pstrProcedureName`  
 \[in\] 要剖析的程序名稱位址。  
  
 `pstrItemName`  
 \[in\] 要寫入內容程序要評估項目名稱的位址。  如果此參數為 `NULL`，程式碼在指令碼引擎的全域內容進行評估。  
  
 `punkContext`  
 \[in\] 內容物件的位址。  這個物件是保留在偵錯環境，這種內容可能由偵錯工具提供表示現用執行階段內容。  如果此參數為， `NULL`引擎使用 `pstrItemName` 識別內容。  
  
 `pstrDelimiter`  
 \[in\] 結束程序符號的位址。  當 `pstrCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如，兩個單引號 \("\)，偵測程序的結尾。  這個參數指定 \(例如使用的主機，允許指令碼引擎提供了一些條件約束基底前置處理符號 \(，取代使用單引號 \(『\) 與兩個單引號做為分隔符號\)。  \(和\)，如果指令碼引擎完全如何利用這項資訊決定指令碼引擎。  如果未使用分隔符號指示的關閉程序，請將這個參數設定為 `NULL` 。  
  
 `dwSourceContextCookie`  
 \[in\] 使用於偵錯用途的應用程式定義的值。  
  
 `ulStartingLineNumber`  
 \[in\] 指定之以零起始的值會解析哪一行開始。  
  
 `dwFlags`  
 \[in\] 旗標與程序。  可以是下列值的組合:  
  
|值|意義|  
|-------|--------|  
|SCRIPTPROC\_ISEXPRESSION|表示 `pstrCode` 的程式碼是表示程序之傳回值的運算式。  根據預設，程式碼可以在程序包含運算式，陳述式指令碼語言允許的清單或另一個屬性。|  
|SCRIPTPROC\_IMPLICIT\_THIS|表示 `this` 指標會併入程序範圍內。|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|表示 `this` 指標的父代 \(Parent\) 是包含在程序的範圍內。|  
  
 `ppdisp`  
 \[in\] 指標位址包含指令碼的全域方法和屬性的物件。  如果指令碼引擎不支援這類物件， `NULL` 傳回。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_NOTIMPL`|不支援這個方法。  指令碼引擎不支援程序的執行階段加入至命名空間。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎會處於未初始化或關閉狀態\)。|  
|`OLESCRIPT_E_SYNTAX`|未指定中的語法錯誤在程序中。|  
|`S_FALSE`|指令碼引擎不支援分派物件; `ppdisp` 參數設定為 `NULL`。|  
  
## 備註  
 在呼叫期間，指令碼不會評估，相反地，會編譯成可從指令碼呼叫之後的指令碼狀態。  
  
## 請參閱  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)