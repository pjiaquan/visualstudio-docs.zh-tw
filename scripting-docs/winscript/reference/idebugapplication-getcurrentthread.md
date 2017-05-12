---
title: "IDebugApplication::GetCurrentThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.GetCurrentThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::GetCurrentThread"
ms.assetid: 15128e77-6fc6-42a2-8c04-20e22ef03f29
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::GetCurrentThread
會傳回執行緒與目前的執行緒。  
  
## 語法  
  
```  
HRESULT GetCurrentThread(  
   IDebugApplicationThread**  pat  
);  
```  
  
#### 參數  
 `pat`  
 \[in\] 執行緒與目前的執行緒。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回執行緒與目前的執行緒。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)