---
title: "IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthorProcedure::ParseProcedureText"
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthorProcedure::ParseProcedureText
剖析編碼的程序，將程式碼加入至程序的文字撰寫的指令碼引擎，並建立對應於編碼程序的 `IScriptEntry` 物件。  
  
## 語法  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### 參數  
 `pszCode`  
 \[in\] 要剖析的指令碼文字。  
  
 `pszFormalParams`  
 \[in\] 型式參數名稱的位址對於程序。  必須由建立的指令碼引擎的適當的分隔符號分隔參數名稱。  在括弧不應該包含名稱。  
  
 `pszProcedureName`  
 \[in\] 要剖析的程序名稱的位址。  
  
 `pszItemName`  
 \[in\] 包含項目名稱與 `IScriptEntry` 物件之緩衝區的位址。  
  
 `pszDelimiter`  
 \[in\] 結束指令碼區塊符號的位址。  當 `pszCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如兩個單引號\)，偵測指令碼區塊的結尾。  如果沒有標記，指令碼區塊的結束符號將此參數設定為 NULL。  
  
 `dwCookie`  
 \[in\] 與新的 `IScriptEntry` 物件的應用程式定義的值。  
  
 `dwFlags`  
 \[in\] 不適用。  
  
 `pdispFor`  
 \[in\] 不適用。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 目前 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎不會執行這個方法。  
  
## 請參閱  
 [IActiveScriptAuthorProcedure 介面](../../winscript/reference/iactivescriptauthorprocedure-interface.md)