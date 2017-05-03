---
title: "IActiveScriptAuthor::GetChars | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetChars"
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IActiveScriptAuthor::GetChars
傳回一組要求的完成內容的完成字元。  
  
## 語法  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### 參數  
 `fRequestedList`  
 \[in\] 要求完成的內容。  
  
|常數|值|描述|  
|--------|-------|--------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|0x0001|要求左側列舉型別。|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|0x0002|要求成員完成的內容。|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|0x0003|要求參數清單。|  
|SCRIPT\_CMPL\_COMMIT|0x0004|要求參數清單的完成。|  
  
 `pbstrChars`  
 \[in\] 對應到要求的完成內容的字元。  
  
|`fRequestedList` 參數|要傳回的字元|  
|-------------------------|------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|"."|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|「\=」|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|\(「，」|  
|SCRIPT\_CMPL\_COMMIT|「\(\)」|  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)