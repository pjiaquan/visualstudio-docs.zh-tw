---
title: "IJsDebugDataTarget::GetTlsValue 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetTlsValue 方法
對於要進行偵錯的執行緒，擷取執行緒區域儲存區 \(TLS\) 位置中所指定 TLS 索引的值。  
  
## 語法  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### 參數  
 `threadId`  
 \[in\] 要讀取的目標處理序中執行的執行緒。  
  
 `tlsIndex`  
 \[in\] 目標處理序呼叫 TlsAlloc 函式時配置的 TLS 索引。  
  
 `pValue`  
 \[out\] 儲存在執行緒的 TLS 位置的指標大小的值。  如果目標執行緒為 32 位元，則此值的上方 32 位元會是零。  
  
## 傳回值  
  
## 備註  
 處理序的每個執行緒都有自己專用於每個 TLS 索引的位置。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)