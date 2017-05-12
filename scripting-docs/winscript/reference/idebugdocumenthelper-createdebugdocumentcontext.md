---
title: "IDebugDocumentHelper::CreateDebugDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.CreateDebugDocumentContext
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::CreateDebugDocumentContext"
ms.assetid: aa4ec691-9fb1-4da7-8085-b40d8a062467
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::CreateDebugDocumentContext
建立新的偵錯資料內容。  
  
## 語法  
  
```  
HRESULT CreateDebugDocumentContext(  
   ULONG                    iCharPos,  
   ULONG                    cChars,  
   IDebugDocumentContext**  ppddc  
);  
```  
  
#### 參數  
 `iCharPos`  
 \[in\] 偵錯資料內容中的開始位置。  
  
 `cChars`  
 \[in\] 字元數量的內容。  
  
 `ppddc`  
 \[in\] 新偵錯資料內容。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法可讓主應用程式建立新的偵錯資料內容。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)