---
title: "IDebugDocumentHelper::GetDebugApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.GetDebugApplicationNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::GetDebugApplicationNode"
ms.assetid: ecd18803-beb4-4ac2-9702-cc9e8a12c395
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::GetDebugApplicationNode
傳回應用程式進行偵錯的節點與文件相對應。  
  
## 語法  
  
```  
HRESULT GetDebugApplicationNode(  
   IDebugApplicationNode**  ppdan  
);  
```  
  
#### 參數  
 `ppdan`  
 \[in\] 與文件相關的應用程式進行偵錯的節點。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 傳回應用程式進行偵錯的節點與文件相對應。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)