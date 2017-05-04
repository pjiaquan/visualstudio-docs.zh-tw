---
title: "IJsDebugStackWalker::GetNext 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker::GetNext 方法
取得下一個畫面格。  
  
## 語法  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### 參數  
 `ppFrame`  
 \[out\] 代表堆疊框架的物件。  
  
## 傳回值  
  
## 備註  
 沒有其他要列舉的堆疊框架時，傳回 E\_JsDEBUG\_OUTSIDE\_OF\_VM  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugStackWalker 介面](../../winscript/reference/ijsdebugstackwalker-interface.md)