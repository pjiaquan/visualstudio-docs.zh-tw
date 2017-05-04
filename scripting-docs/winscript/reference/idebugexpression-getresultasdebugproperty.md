---
title: "IDebugExpression::GetResultAsDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsDebugProperty
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsDebugProperty"
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsDebugProperty
傳回運算式評估的結果做為偵錯屬性和作業的傳回值。  
  
## 語法  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### 參數  
 `phrResult`  
 \[in\] 作業的傳回值。  
  
 `ppdp`  
 \[in\] 運算式的偵錯屬性。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|作業暫止。|  
  
## 備註  
 這個方法會傳回要評估的運算式結果為 `IDebugProperty` 和作業的 `HRESULT`。  
  
 這個方法會傳回 `S_OK` ，並 `phrResult` 傳回 `E_ABORT` ，如果 `Abort` 中止作業。  
  
## 請參閱  
 [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)