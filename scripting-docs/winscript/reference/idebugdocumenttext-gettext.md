---
title: "IDebugDocumentText::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetText"
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetText
擷取字元和字元與屬性關聯的字元位置範圍。  
  
## 語法  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### 參數  
 `cCharacterPosition`  
 \[in\] 開始字元位置範圍內的位置。  
  
 `pcharText`  
 \[in， out\] A 字元文字緩衝區。  緩衝區的大小必須足以容納 `cMaxChars` 字元。  如果這個參數為 null，則方法會傳回字元。  
  
 `pstaTextAttr`  
 \[in， out\] A 字元屬性緩衝區。  緩衝區的大小必須足以容納 `cMaxChars` 字元。  如果這個參數為 null，則方法會傳回屬性。  
  
 `pcNumChars`  
 \[in， out\] 字元\/屬性數目會傳回。  必須將這個參數設為零在呼叫之前這個方法。  
  
 `cMaxChars`  
 \[in\] 字元數位在字元位置的範圍。  同時指定字元的最大數目會傳回。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會擷取字元和 \(或\) 字元與屬性關聯的字元位置範圍。  字元位置範圍都是字元位置和大量字元指定。  
  
## 請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE\_TEXT\_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)