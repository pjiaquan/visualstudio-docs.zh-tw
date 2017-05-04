---
title: "IDebugApplication::QueryCurrentThreadIsDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.QueryCurrentThreadIsDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::QueryCurrentThreadIsDebuggerThread"
ms.assetid: e22ad8a4-a8be-423d-80f2-28256a7448ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::QueryCurrentThreadIsDebuggerThread
判斷目前執行中的執行緒是偵錯工具執行緒。  
  
## 語法  
  
```  
HRESULT QueryCurrentThreadIsDebuggerThread();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法會成功，而且目前執行中的執行緒是偵錯工具執行緒。|  
|`S_FALSE`|目前執行中的執行緒不是偵錯工具執行緒。|  
  
## 備註  
 這個方法會判斷目前執行中的執行緒是偵錯工具執行緒。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)