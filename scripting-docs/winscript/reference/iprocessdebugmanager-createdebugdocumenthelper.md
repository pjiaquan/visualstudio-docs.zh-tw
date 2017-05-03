---
title: "IProcessDebugManager::CreateDebugDocumentHelper | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateDebugDocumentHelper
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateDebugDocumentHelper"
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateDebugDocumentHelper
建立新的偵錯該應用程式的文件 Helper。  
  
## 語法  
  
```  
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### 參數  
 `punkOuter`  
 \[in\]，如果傳回的物件將會彙總， `punkOuter` 是介面指標至控制項 `IUnknown`。  否則，它是 null 指標。  
  
 `pddh`  
 \[out\] 此應用程式的偵錯資料的 Helper 物件。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會建立新的偵錯該應用程式的文件 Helper。  
  
## 請參閱  
 [IProcessDebugManager 介面](../../winscript/reference/iprocessdebugmanager-interface.md)