---
title: "IEnumJsStackFrames::Next 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames::Next 方法
取得指定之數目的畫面格。  
  
## 語法  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### 參數  
 `cFrameCount`  
 \[in\] 要取得的畫面格數目。  
  
 `pFrames`  
 \[out\] 用來儲存畫面格的陣列。  
  
 `pcFetched`  
 \[out\] 傳回的畫面格數目。  
  
## 傳回值  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IEnumJsStackFrames 介面](../../winscript/reference/ienumjsstackframes-interface.md)