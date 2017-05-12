---
title: "IDebugDocumentHelper::BringDocumentContextToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.BringDocumentContextToTop
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::BringDocumentContextToTop"
ms.assetid: cf9751c5-e9b7-45c6-b084-3f3873dbf01d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::BringDocumentContextToTop
提供在偵錯工具使用者介面的最頂端文件內容。  
  
## 語法  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### 參數  
 `pddc`  
 文件內容給在偵錯工具使用者介面的最頂端。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會在偵錯工具使用者介面的最頂端文件內容。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)