---
title: "IDebugExpression::GetResultAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsString"
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsString
傳回運算式評估結果為字串和作業的傳回值。  
  
## 語法  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### 參數  
 `phrResult`  
 \[in\] 作業的傳回值。  
  
 `pbstrResult`  
 \[in\] 要評估的運算式結果。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|作業暫止。|  
  
## 備註  
 這個方法會傳回要評估的運算式結果為字串和作業的 `HRESULT`。  
  
 這個方法會傳回 `S_OK` ，並 `phrResult` 傳回 `E_ABORT` ，如果 `Abort` 中止作業。  
  
## 請參閱  
 [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)