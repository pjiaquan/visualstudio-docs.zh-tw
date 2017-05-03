---
title: "IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetInfoFromContext"
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::GetInfoFromContext
傳回型別資訊和錨定特定字元的位置在程式碼區塊。  這個成員的 IntelliSense，全域清單和參數有關的資訊。  
  
## 語法  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### 參數  
 `pszCode`  
 \[in\] 要用的程式碼區塊會產生字串的位址資訊時發生。  
  
 `cchCode`  
 \[in\] 程式碼區塊的長度。  
  
 `ichCurrentPosition`  
 \[in\] 相對區塊的起始字元位置。  
  
 `dwListTypesRequested`  
 \[in\] 要求的清單類型。  可以是下列值的組合:  
  
|常數|值|描述|  
|--------|-------|--------|  
|SCRIPT\_CMPL\_NOLIST|0x0000|如果沒有任何清單。|  
|SCRIPT\_CMPL\_MEMBERLIST|0x0001|成員清單。|  
|SCRIPT\_CMPL\_ENUMLIST|0x0002|列舉清單。|  
|SCRIPT\_CMPL\_PARAMLIST|0x0004|呼叫方法的參數清單。|  
|SCRIPT\_CMPL\_GLOBALLIST|0x0008|全域清單。|  
  
 SCRIPT\_CMPL\_GLOBALLIST 型別視為可合併使用或運算子與其他完成項目的預設完成項目。  撰寫引擎的指令碼會先嘗試填入其他完成清單項目的型別資訊。  如果失敗，引擎會 SCRIPT\_CMPL\_GLOBALLIST 填入。  
  
 `pdwListTypesProvided`  
 \[in\] 提供清單的型別。  
  
 `pichListAnchorPosition`  
 \[in\] 包含目前位置內容的起始索引。  起始索引是相對於區塊的開頭。  
  
 只有在 `dwListTypesRequested` ，包括 SCRIPT\_CMPL\_MEMBERLIST、SCRIPT\_CMPL\_ENUMLIST 或時，這個 SCRIPT\_CMPL\_GLOBALLIST 填入。  對於其他需求的清單型別，則結果會是未定義的。  
  
 `pichFuncAnchorPosition`  
 \[in\] 包含目前位置函式呼叫的起始索引。  起始索引是相對於區塊的開頭。  
  
 這個填入，只有當包含目前位置的中的內容是函式呼叫中，如此一來，當 `dwListTypesRequested` ，包括 SCRIPT\_CMPL\_PARAMLIST 時。  否則，結果是未定義的。  
  
 `pmemid`  
 \[in\] 此函式的 MEMBERID，如所定義 `IProvideMultipleClassInfo``ppunk` 參數的型別。  
  
 只有在 `dwListTypesRequested` ，包括 SCRIPT\_CMPL\_PARAMLIST 時，會填入。  
  
 `piCurrentParameter`  
 \[in\] 包含目前位置參數的索引。  如果目前位置在函式名稱，則傳回\-1。  
  
 只有在 `dwListTypesRequested` ，包括 SCRIPT\_CMPL\_PARAMLIST 時， `piCurrentParameter` 值填入。  
  
 `ppunk`  
 型別資訊， `IProvideMultipleClassInfo` 以物件的形式，提供。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideMultipleClassInfo>   
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)