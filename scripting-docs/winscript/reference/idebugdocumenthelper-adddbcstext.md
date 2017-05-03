---
title: "IDebugDocumentHelper::AddDBCSText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDBCSText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDBCSText"
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDBCSText
DBCS 字串附加至文件的結尾。  
  
## 語法  
  
```  
HRESULT AddDBCSText(  
   LPCSTR  pszText  
);  
```  
  
#### 參數  
 `pszText`  
 \[out\] 包含文字之 null 結尾字串的指標。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|方法無法將字元。|  
  
## 備註  
 這個方法會產生 `IDebugDocumentTextEvents` 告知。  
  
> [!NOTE]
>  如果呼叫這個方法，在 `IDebugDocumentHelper::AddDeferredText` 呼叫之後， `E_FAIL` 傳回。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents 介面](../../winscript/reference/idebugdocumenttextevents-interface.md)