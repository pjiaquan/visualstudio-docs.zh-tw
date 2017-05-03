---
title: "IActiveScriptDebug::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptTextAttributes"
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptTextAttributes
傳回指令碼任意文字區塊的文字屬性變更為。  
  
## 語法  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### 參數  
 `pstrCode`  
 \[in\] 指令碼區塊文字。  不需要是以 null 結束之字串。  
  
 `uNumCodeChars`  
 \[in\] 字元數指令碼區塊的文字。  
  
 `pstrDelimiter`  
 \[in\] 結束指令碼區塊符號的位址。  當 `pstrCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如，兩個單引號 \("\)，偵測指令碼區塊的結尾。  這個參數指定 \(例如使用的主機，允許指令碼引擎提供了一些條件約束基底前置處理符號 \(，取代使用單引號 \(『\) 與兩個單引號做為分隔符號\)。  \(和\)，如果指令碼引擎正確方式使用這項資訊決定指令碼引擎。  如果未使用分隔符號指示指令碼區塊的結尾，請將此參數設定為 NULL。  
  
 `dwFlags`  
 \[in\] 旗標與指令碼區塊。  可以是下列值的組合:  
  
|常數|值|描述|  
|--------|-------|--------|  
|GETATTRTYPE\_DEPSCAN|0x0001|分別表示識別項和點運算子應該識別與 SOURCETEXT\_ATTR\_IDENTIFIER，並 SOURCETEXT\_ATTR\_MEMBERLOOKUP 旗標。|  
|GETATTRFLAG\_THIS|0x0100|表示應該識別目前物件的識別項與 SOURCETEXT\_ATTR\_THIS 旗標。|  
|GETATTRFLAG\_HUMANTEXT|0x8000|表示應該識別字串內容和註解文字 SOURCETEXT\_ATTR\_HUMANTEXT 旗標。|  
  
 `pattr`  
 \[in， out\] 包含所傳回之屬性的緩衝區。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 實作介面的 `IDebugDocumentText` 智慧型主機可以使用這個方法將呼叫委派給 `IDebugDocumentText::GetText` 方法。  
  
 指令碼區塊的這個方法; `GetScriptletTextAttributes` 方法是 Scriptlet。  
  
## 請參閱  
 [IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE\_TEXT\_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)