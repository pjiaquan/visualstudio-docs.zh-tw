---
title: "IDebugSyncOperation::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.Execute
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::Execute"
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::Execute
同步執行作業並傳回。  
  
## 語法  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### 參數  
 `ppunkResult`  
 \[in\] 物件參數作業會傳回。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_ABORT`|作業可以藉由呼叫方法 `IDebugSyncOperation::InProgressAbort` 中止。|  
  
## 備註  
 同步處理序偵錯目標執行緒呼叫的處理常式 `Execute` 方法。  
  
## 請參閱  
 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)