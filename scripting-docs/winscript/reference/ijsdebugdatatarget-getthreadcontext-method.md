---
title: "IJsDebugDataTarget::GetThreadContext 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetThreadContext 方法
擷取指定之執行緒的內容。  
  
## 語法  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### 參數  
 `threadId`  
 \[in\] 目標處理序中執行的執行緒。  
  
 `contextFlags`  
 \[in\] 指定內容旗標。  這和 CONTEXT 的 ContextFlags 欄位相同 \(如需詳細資訊，請參閱 winnt.h，搜尋 CONTEXT\_ALL\)。  
  
 `contextSize`  
 \[in\] pContext 所指定的緩衝區大小。  
  
 `pContext`  
 \[out\] 接收特定平台的內容結構至 pContext 指定的緩衝區。  
  
## 傳回值  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)