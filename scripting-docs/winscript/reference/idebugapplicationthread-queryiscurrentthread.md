---
title: "IDebugApplicationThread::QueryIsCurrentThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.QueryIsCurrentThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::QueryIsCurrentThread"
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::QueryIsCurrentThread
判斷這個執行緒是目前執行的執行緒。  
  
## 語法  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法會成功，而且這是目前執行的執行緒。|  
|`S_FALSE`|這不是目前執行的執行緒。|  
  
## 備註  
 這個方法會判斷這個執行緒是目前執行的執行緒。  
  
## 請參閱  
 [IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)