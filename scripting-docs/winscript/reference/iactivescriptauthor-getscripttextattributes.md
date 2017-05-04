---
title: "IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptTextAttributes"
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetScriptTextAttributes
傳回指令碼區塊的文字屬性變更為。  
  
## 語法  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### 參數  
 `pszCode`  
 \[in， size\_is \(`cch`\)\]。指令碼區塊的文字。  不需要是以 null 結束之字串。  
  
 `cch`  
 \[out\] 用來 `pszCode` 和 `pattr` 參數的大小。  
  
 `pszDelimiter`  
 \[in\] 結束指令碼符號的位址。  當 `pszCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如兩個單引號\)， scriptlet 偵測到的結尾。  如果沒有識別指令碼區塊，結尾的符號將此參數設定為 NULL。  
  
 `dwFlags`  
 \[in\] 與指令碼區塊的文字屬性的旗標。  可以是下列值的組合:  
  
|常數|值|描述|  
|--------|-------|--------|  
|GETATTRTYPE\_DEPSCAN|0x0001|識別具有 SOURCETEXT\_ATTR\_IDENTIFIER 屬性的識別項，並識別具有 SOURCETEXT\_ATTR\_MEMBERLOOKUP 屬性中使用點運算子。|  
|GETATTRFLAG\_THIS|0x0100|識別具有 SOURCETEXT\_ATTR\_THIS 屬性目前的物件。|  
|GETATTRFLAG\_HUMANTEXT|0x8000|識別字串內容和註解。SOURCETEXT\_ATTR\_HUMANTEXT 具有屬性的文字。|  
  
 `pattr`  
 \[in, out, size\_is\(`cch`\)\] 指令碼會封鎖程式碼的色彩資訊。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE\_TEXT\_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)