---
title: "IJsDebugProcess::CreateStackWalker 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProcess::CreateStackWalker 方法
堆疊查核器的 Factory 方法。  
  
## 語法  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### 參數  
 `threadId`  
 \[in\] 執行緒 ID。  
  
 `ppStackWalker`  
 \[out\] 新的堆疊查核器物件。  
  
## 傳回值  
  
## 備註  
 如果執行緒沒有 JavaScript，則傳回 E\_JsDEBUG\_UNKNOWN\_THREAD。  這個方法只能在目標處理序停止時呼叫。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugProcess 介面](../../winscript/reference/ijsdebugprocess-interface.md)