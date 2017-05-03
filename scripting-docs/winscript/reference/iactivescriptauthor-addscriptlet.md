---
title: "IActiveScriptAuthor::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddScriptlet"
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::AddScriptlet
將程式碼 scriptlet 做為根層級 `IScriptNode` 物件的子系。  在主應用程式， scriptlet 完整名稱只允許有兩個層級。  
  
## 語法  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### 參數  
 `pszDefaultName`  
 \[in\] 要與相關聯的預設名稱的地址。scriptlet。  
  
 `pszCode`  
 \[in\] scriptlet 文字的位址。  
  
 `pszItemName`  
 \[in\] 完整名稱的 scriptlet 最上層識別項之緩衝區的位址在主應用程式。  
  
 `pszSubItemName`  
 \[in\] 完整名稱的 scriptlet 第二層項目識別項的緩衝區的位址在主應用程式。  此名稱，則只有一個層級，則設為 null。  
  
 `pszEventName`  
 \[in\] 包含事件名稱 scriptlet 是一個事件處理常式緩衝區的位址。  
  
 `pszDelimiter`  
 \[in\] 結束指令碼區塊符號的位址。  當 `pszCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如兩個單引號\)，偵測指令碼區塊的結尾。  符號，則不會將指令碼區塊的結尾，請將此參數設定為 NULL。  
  
 `dwCookie`  
 \[in\] 用來使 scriptlet 與主應用程式物件的應用程式定義的值。  
  
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