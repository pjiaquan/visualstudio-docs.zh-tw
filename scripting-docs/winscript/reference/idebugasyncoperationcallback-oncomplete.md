---
title: "IDebugAsyncOperationCallBack::onComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperationCallBack.onComplete
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugAsyncOperationCallBack::onComplete"
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperationCallBack::onComplete
信號結果從非同步取得偵錯作業。  
  
## 語法  
  
```  
HRESULT onComplete();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會指示結果 `IDebugAsyncOperation` 從物件取得。  在偵錯工具執行緒上引發事件。  
  
## 請參閱  
 [IDebugAsyncOperationCallBack 介面](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)