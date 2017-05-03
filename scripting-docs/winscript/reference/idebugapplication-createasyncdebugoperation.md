---
title: "IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateAsyncDebugOperation"
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateAsyncDebugOperation
提供對指定同步處理非同步存取偵錯作業。  
  
## 語法  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### 參數  
 `psdo`  
 \[in\] 偵錯作業同步處理物件。  
  
 `ppado`  
 \[in\] 非同步偵錯管理物件。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法允許語言引擎評估運算式以非同步方式，而不必明確地同步使用偵錯工具執行緒。  如需詳細資訊，請參閱 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)和 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)