---
title: "IApplicationDebugger::QueryAlive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.QueryAlive
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::QueryAlive"
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::QueryAlive
表示偵錯工具是否敏感。  
  
## 語法  
  
```  
HRESULT QueryAlive();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會指示偵錯工具是否敏感。  這個方法的實作必須傳回 `S_OK`。  
  
 如果偵錯工具處理序意外結束， COM 會從修剪的 Proxy 的錯誤呼叫對這個方法。  
  
## 請參閱  
 [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)