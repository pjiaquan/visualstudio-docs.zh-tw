---
title: "IJsDebugFrame::GetReturnAddress 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetReturnAddress
apilocation: jscript9diag.dll
ms.assetid: 7f10c1d6-d7b9-402e-9020-04cded37f9d3
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetReturnAddress 方法
取得在框架的 "start" \(請參閱 GetStackRange\) 位置推入的傳回位址。  
  
## 語法  
  
```  
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### 參數  
 `pReturnAddress`  
 \[out\] 傳回位址。  
  
## 傳回值  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)