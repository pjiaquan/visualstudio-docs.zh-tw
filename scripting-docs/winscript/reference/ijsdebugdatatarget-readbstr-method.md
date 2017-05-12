---
title: "IJsDebugDataTarget::ReadBSTR 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadBSTR 方法
從偵錯目標讀取 BSTR。  
  
## 語法  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### 參數  
 `address`  
 \[in\] 要用於讀取的位址。  
  
 `pString`  
 \[out\] 從偵錯目標讀取的 BSTR。  
  
## 傳回值  
  
## 備註  
 如果位址無效，則傳回 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)