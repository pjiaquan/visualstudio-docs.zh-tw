---
title: "IDebugDocumentText::GetLineOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetLineOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetLineOfPosition"
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetLineOfPosition
傳回行號，且，或者，字元位移 \(Offset\) 對應於指定之字元位置的程式碼行中。  
  
## 語法  
  
```  
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### 參數  
 `cCharacterPosition`  
 \[in\] 開始字元位置範圍內的位置。  
  
 `pcLineNumber`  
 \[in\] 範圍的行號。  
  
 `pcCharacterOffsetInLine`  
 \[in， out\] 範圍內的字元位移 `pcLineNumber`在行中的位置。  如果此參數為 `NULL`，方法不會傳回值。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回行號，且，或者，字元位移 \(Offset\) 對應於指定之字元位置的程式碼行中。  
  
## 請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)