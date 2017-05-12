---
title: "IDebugDocumentProvider::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentProvider.GetDocument
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentProvider::GetDocument"
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider::GetDocument
如果檔案不存在，讓文件具現化。  
  
## 語法  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### 參數  
 `ppssd`  
 \[in\] 與文件相關的偵錯資料。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 如果檔案不存在，這個方法會導致文件具現化。  
  
## 請參閱  
 [IDebugDocumentProvider 介面](../../winscript/reference/idebugdocumentprovider-interface.md)