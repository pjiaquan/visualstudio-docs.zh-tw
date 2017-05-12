---
title: "IJsDebugFrame::GetStackRange 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetStackRange 方法
傳回邏輯 JavaScript 堆疊框架的絕對位址範圍。  
  
## 語法  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### 參數  
 `pStart`  
 \[out\] 將圖文框的多數堆疊指標置於最下方。  
  
 `pEnd`  
 \[out\] 將圖文框的多數堆疊指標置於最上方。  
  
## 傳回值  
  
## 備註  
 這個方法對於拼湊從多個執行階段收集的交錯堆疊追蹤會很有用。  開始、結束堆疊指標可能包含多個實體機器堆疊框架 \(解譯的 JavaScript 執行階段架構\)。當堆疊從高位址向低位址成長時，開始 \> 結束。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)