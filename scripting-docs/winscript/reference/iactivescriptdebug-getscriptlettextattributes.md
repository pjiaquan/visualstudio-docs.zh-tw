---
title: "IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptletTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptletTextAttributes"
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptletTextAttributes
傳回隨機 scriptlet 文字屬性。  
  
## 語法  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### 參數  
 `pstrCode`  
 \[in\] scriptlet 文字。  不需要是以 null 結束之字串。  
  
 `uNumCodeChars`  
 \[in\] 的字元數。scriptlet 文字的。  
  
 `pstrDelimiter`  
 \[in\] 位址結束 scriptlet 符號。  當 `pstrCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如，兩個單引號 \("\)， scriptlet 偵測到的結尾。  這個參數指定 \(例如使用的主機，允許指令碼引擎提供了一些條件約束基底前置處理符號 \(，取代使用單引號 \(『\) 與兩個單引號做為分隔符號\)。  \(和\)，如果指令碼引擎正確方式使用這項資訊決定指令碼引擎。  如果未使用分隔符號 scriptlet 指令的結束，請將此參數設定為 NULL。  
  
 `dwFlags`  
 \[in\] 旗標與 scriptlet。  可以是下列值的組合:  
  
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
  
 這個呼叫，因為 Scriptlet 比指令碼區塊時，經常會是運算式，而且可能會有不同的語法提供。  如果有相同的語法，這個方法的實作與 `GetScriptTextAttributes` 方法的實作都會相同。  
  
## 請參閱  
 [IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE\_TEXT\_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)