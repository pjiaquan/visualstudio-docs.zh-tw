---
title: "IDebugDocumentHelper::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Attach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Attach"
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Attach
若要將文字加入至文件樹狀結構。  
  
## 語法  
  
```  
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### 參數  
 `pddhParent`  
 \[in\] 要加入文件的文件樹狀結構。  可能是 NULL。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會將文件加入至文件樹狀結構，使用 `pddhParent` 做為父代。  如果 `pddhParent` 是 `NULL`，文件將會是最上層資料。  
  
## 請參閱  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)