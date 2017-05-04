---
title: "IJsDebugBreakPoint::Disable 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.Disable
apilocation: jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::Disable 方法
停用中斷點。  
  
## 語法  
  
```  
HRESULT Disable(void);  
```  
  
## 傳回值  
  
## 備註  
 如果在刪除的中斷點上呼叫，則傳回 E\_UNEXPECTED。  如果在已經停用的中斷點上呼叫，則傳回 S\_FALSE。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugBreakPoint 介面](../../winscript/reference/ijsdebugbreakpoint-interface.md)