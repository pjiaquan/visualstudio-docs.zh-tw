---
title: "IActiveScriptAuthor::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::ParseScriptText"
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::ParseScriptText
解析指令碼文字，將文字加入至撰寫的指令碼引擎，並建立對應於指令碼區塊的 `IScriptEntry` 物件。  
  
## 語法  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### 參數  
 `pszCode`  
 \[in\] 要剖析的指令碼文字。  
  
 `pszItemName`  
 \[in\] 包含項目名稱與指令碼區塊的緩衝區的位址。  
  
 `pszDelimiter`  
 \[in\] 結束指令碼區塊符號的位址。  當 `pszCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如兩個單引號\)，偵測指令碼區塊的結尾。  如果沒有識別指令碼區塊，結尾的符號將此參數設定為 NULL。  
  
 `dwCookie`  
 \[in\] 與新的 `IScriptEntry` 物件的應用程式定義的值。  
  
 `dwFlags`  
 \[in\] 不適用。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)